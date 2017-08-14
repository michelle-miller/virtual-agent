---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-10"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Implémentation de capacités de base 
{: #impl_intents}

Découvrez les tâches de développement à effectuer pour prendre en charge les types de réponse sélectionnés pour certaines capacités.
{: shortdesc}

Etudiez la manière dont vous souhaitez gérer les capacités suivantes, au minimum :

- ***None of the above (Aucun des choix ci-dessus)***

    La réponse que vous définissez pour cette capacité est renvoyée aux utilisateurs chaque fois qu'ils saisissent une entrée que le système ne peut pas reconnaître et mapper à une capacité activée. En conséquence, elle peut être souvent présentée aux utilisateurs, surtout si vous n'activez pas beaucoup de capacités. Pensez à la manière dont vous souhaitez que l'agent virtuel réponde. Une réponse textuelle telle que *Désolé. Je ne comprend pas votre demande.* suffit. Si vous souhaitez que les utilisateurs puissent contacter un agent humain, vous pouvez inclure le texte *Entrez 'agent' pour être transféré vers un agent humain.* Cette entrée déclenche l'événement `agent`, qui est expliqué ci-dessous. Pour plus d'informations, voir [Utilisation de la capacité None of the above (Aucun des choix ci-dessus)](impl_intents.html#none-of-the-above).

- **La capacité *Connect to agent (Se connecter à l'agent* et toutes les capacités avec le type de réponse *Transfer to human agent (Transférer vers un agent humain)***

    Ces capacités transfèrent l'utilisateur à un agent humain. Vous devez ajouter la logique qui transfère la conversation à votre support technique. L'une des approches que vous pouvez adopter consiste à ajouter une logique qui se
connecte à un service externe déjà utilisé pour gérer les demandes entrantes sur votre site de service clients. Les problèmes que l'agent virtuel ne peut résoudre peuvent être transférés à votre
support technique dans leur file d'attente de demandes d'assistance existante afin
qu'ils soient classés par priorité et résolus. Pour implémenter la logique de transfert,
écoutez l'événement `agent` et définissez les fonctions à effectuer lorsque l'événement est
déclenché. Pour des idées, voir [dwAnswers![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://developer.ibm.com/answers/search.html?f=&amp;type=question&amp;redirect=search/search&amp;q=watson-virtual-agent&amp;q=human "icône Lien externe"){: new_window}.

- **Capacités avec le type de réponse *Built-in (Intégré)***

    Si vous conservez les paramètres par défaut pour les capacités de base
configurées pour utiliser le type de réponse Use built-in conversation (Utiliser la conversation intégrée) et que ces capacités sont
activées, vous devez ajouter une logique pour prendre en charge l'échange d'informations
et les transactions métier traités par les conversations intégrées. Pour plus de
détails, voir [Implémentation de la logique de prise en charge de la conversation intégrée](impl_intents.html#backend_transaction).

- **Capacités avec le type de réponse *Use your own conversation (Utiliser votre propre conversation)***

    Pour les capacités complexes qui requièrent un dialogue personnalisé pour gérer l'échange d'informations avec l'utilisateur, vous pouvez écrire un dialogue à l'aide du service {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Pour plus de détails, voir [Ajout de dialogues personnalisés pour les capacités de base](add-custom-dialog.html).

## Implémentation de la logique de prise en charge de la conversation intégrée
{: #backend_transaction}

Découvrez comment échanger des informations et effectuer des processus métier qui
peuvent se produire lorsque des utilisateurs interagissent avec des capacités configurées
pour utiliser la conversation intégrée.

### A propos de cette tâche

Certaines des capacités de base configurées pour utiliser le type de réponse de la conversation intégrée par défaut peuvent traiter les processus métier. Votre application doit pouvoir enregistrer la transaction auprès des systèmes d'enregistrement dorsaux.

- Si vous implémentez le widget de discussion {{site.data.keyword.IBM_notm}} fourni, il reconnaît les événements déclenchés par certaines réponses utilisateur. Toutefois, des étapes supplémentaires sont à effectuer pour écouter ces événements dans votre
application afin que vous puissiez effectuer les transactions initiées sur vos systèmes dorsaux.
- Si vous n'utilisez pas le widget de discussion fourni, vous devez vous assurer
que votre interface utilisateur personnalisée peut reconnaître les événements déclenchés par les flux de conversation intégrée
et les traiter de manière appropriée.

Examinez le [processus du flux de dialogue Make a payment (Effectuer un paiement)](backend_payment_gif.html#backend_payment_gif) pour un exemple de stockage des variables de carte de crédit privées. 

Par exemple, avec la capacité **Update address (Mettre à jour l'adresse)**, un utilisateur peut changer l'adresse de facturation sur son compte. Vous devez écrire le code qui extrait la nouvelle adresse de Virtual Agent et met à
jour le compte de l'utilisateur sur votre système d'enregistrement avec les nouvelles
informations.

Notez bien que le seul objectif d'un dialogue est de collecter des informations de l'utilisateur. Ces informations sont stockées de l'une des deux manières suivantes :

- Les informations non sensibles ou privées sont stockées dans le contexte du dialogue, un objet de données disponible à la fois pour le bot et votre application.
- Les informations sensibles ou privées (telles que les numéros de carte de crédit) sont stockées dans des variables privées, accessibles uniquement par votre application et non transmises au bot.

### Procédure

Pour implémenter intégralement les transactions commerciales déclenchées à partir de capacités avec des réponses de la conversation intégrée, procédez comme suit :

1.  Ajoutez à votre application une logique qui extrait du système dorsal les informations de profil de l'utilisateur actuel à afficher dans la fenêtre de discussion avant que ces dernières ne soient modifiées. Par exemple, montrer aux utilisateurs un solde de compte avant qu'ils n'effectuent un règlement.

    Utilisez l'action `getUserProfileVariables`. Cette action extrait les variables et les définit dans le profil.

    ```java
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     var variables = data.message.action.args.variables; // spécifiez les variables à extraire dans cette matrice
       for (var i = 0; i < variables.length; i++) {
           var value = something(variables[i])
           /*Effectuez une opération pour extraire la valeur des variables[i]. Il peut s'agir d'un appel ajax ou d'une extraction de
           données de cookies locaux. En fonction de l'emplacement dans lequel vous avez stocké les informations.*/
           window.IBMChat.profile.set(variables[i], value);
       }
       IBMChat.sendSilently('success'); // ou cancel ou failure
    });
    ```
    {: screen}

    Cet exemple utilise un appel REST pour obtenir des informations sur le solde et la date d'échéance d'une facture.

    ```java
    var xmlHttp = new XMLHttpRequest();
      xmlHttp.onreadystatechange = function() {
        if (xmlHttp.readyState == 4 &&  xmlHttp.status == 200)
          callback(xmlHttp.responseText);
      }
      xmlHttp.open("GET", url, true);
      xmlHttp.send(null);
    }
    /* Extrayez des informations de la base de données dorsale et ajoutez-les
    au profil avec IBMChat.profile.set(). */
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     /*
     data = {
       message: {
          text: ['some text'],
                action: {
                     name: 'getUserProfileVariables',
                     args: {
                         variables: [
                    "bill_amount",
                    "payment_due_date"
                ]
                     }
                }
       }

     }
     */

     httpGetAsync('http://yourdomain.com/userprofile', function(user) {
       /* L'enregistrement sur le système dorsal peut renvoyer des informations telles que les suivantes :
       user = {
         "bill_amount": 42.01,
         "payment_due_date": "11/24/2008"
       }
       */
       var variables = data.message.action.args.variables;
       for (var i = 0; i < variables.length; i++) {
         var value = user[variables[i]]);
         window.IBMChat.profile.set(variables[i], value);
       /* Le widget de discussion peut maintenant utiliser les valeurs qu'il a extraites du service dorsal. */
       }
       IBMChat.sendSilently('success'); // ou cancel ou failure
     });
    });
    ```
    {: screen}

 Ajoutez à votre application une logique qui écoute l'action à l'origine du processus métier, puis effectue le processus métier.

    Pour une liste des actions associées à des capacités disposant de types de réponses de la conversation intégrée, voir [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action "icône Lien externe"){: new_window}.

#### Make a payment (Effectuer un paiement)
{: #makeapayment}

Effectuez les étapes ci-après pour implémenter un code qui prend en charge cette transaction.
1.  Votre application doit extraire le solde actuel de l'utilisateur et la date d'échéance du système dorsal. Utilisez la méthode `action:getUserProfileVariables` et définissez les variables `bill_amount` et `payment_due_date` dans le magasin de profils.
1. Votre application doit écouter l'événement `payBill` et définir la logique à effectuer lorsque l'événement est déclenché.
1. Votre application doit également écouter l'événement `sendPaymentReceipt` et définir la logique à effectuer lorsque l'événement est déclenché.

#### Update address (Mettre à jour l'adresse)
{: #updateaddress}

1. Le widget de discussion utilise une présentation de formulaire pour demander la nouvelle adresse de l'utilisateur et la stocke automatiquement dans le profil. Il stocke les variables de profil suivantes :

    ```java
    user_street_address1
    user_street_address2
    user_locality
    user_state_or_province
    user_zipcode
    ```
    {: screen}

1.  Votre application doit écouter l'événement `updateAddress`.

    ```java
    IBMChat.subscribe('action:updateAddress', function(data) {<your-code>}
    ```
    {: screen}

    Définissez une fonction qui extrait et envoie la nouvelle adresse et le type d'adresse (`address_type`) au système dorsal lorsque l'action `updateAddress` est déclenchée.

    Pour collecter des données comportant de nombreuses valeurs, telles que l'adresse postale, vous pouvez utiliser la présentation de formulaire intégrée au widget de discussion. Les utilisateurs entrent des valeurs dans plusieurs zones, puis soumettent le formulaire complet. Par exemple, pour envoyer la nouvelle adresse à votre site via un appel REST POST, vous pouvez utiliser une logique telle que la suivante :

    ```java
    /* Lorsqu'un utilisateur saisit des informations dans un formulaire, elles sont automatiquement ajoutées au profil de l'utilisateur. Donc un flux type peut par exemple inclure une présentation de formulaire dans la fenêtre de discussion, puis appeler cette action une fois que le formulaire a été soumis */
    IBMChat.subscribe('action:updateAddress', function(data) {
      var record = {
        "first_name": IBMChat.profile.get('first_name'),
        "last_name": IBMChat.profile.get('last_name'),
        "user_street_address1": IBMChat.profile.get('user_street_address1'),
        "user_street_address2": IBMChat.profile.get('user_street_address2'),
        "user_locality": IBMChat.profile.get('user_locality'),
        "user_state_or_province": IBMChat.profile.get('user_state_or_province'),
        "user_zipcode": IBMChat.profile.get('user_zipcode')
      };
      httpPostAsync('/updateRecord/', record, function(err, response) {
        if (err) IBMChat.receive('There was an error updating the address.');
      });
    });
    ```
    {: screen}

    Pour plus d'informations sur les présentations intégrées, voir [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout ![icône Lien externe](../../icons/launch-glyph.svg "icône Lien externe")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout "icône Lien externe"){: new_window}.

#### Update contact phone number (Mettre à jour le numéro de téléphone de contact)
{: #updatephone}

1. Le widget de discussion utilise une présentation de formulaire pour demander le nouveau numéro de téléphone de l'utilisateur et le stocke automatiquement dans le profil. Il stocke les variables de profil suivantes :

    ```java
    user_phone_number
    phone_number_type
    ```
    {: screen}

1. Votre application doit écouter l'événement `updatePhoneNumber` et définir la logique permettant de recevoir et d'envoyer le nouveau numéro de téléphone et son type au système dorsal lorsque l'événement est déclenché.

#### Update email (Mettre à jour l'adresse électronique)
{: #updateemail}

1. Le widget de discussion utilise une présentation de formulaire pour demander la nouvelle adresse électronique de l'utilisateur et la stocke automatiquement dans le profil. Il stocke les variables de profil suivantes :

    ```java
    user_email_address
    email_type
    ```
    {: screen}

1. Votre application doit écouter l'événement `updateEmail` et définir la logique permettant de recevoir et d'envoyer la nouvelle adresse électronique au système dorsal lorsque l'événement est déclenché. Elle envoie également des informations sur les types de notification pour lesquels la nouvelle adresse doit être utilisée (`email_type`).

## Utilisation de la capacité None of the above (Aucun des choix ci-dessus)
{: #none-of-the-above}

Découvrez comment la capacité **None of the above (Aucun des choix ci-dessus)** est utilisée par l'agent virtuel.

Contrairement à toutes les autres capacités de base, la capacité **None of the above (Aucun des choix ci-dessus)** ne peut pas être désactivée. En effet, elle sert de fourre-tout pour les énoncés mappés à aucune des capacités configurées. Cette fonctionnalité est utile car vous pouvez fournir une réponse standard, comme *Je ne peux pas vous aider*, pour les demandes utilisateur de capacités dont votre agent ne dispose pas encore. Elle permet également de répondre à des questions absurdes que les clients posent parfois pour s'amuser lorsqu'ils commencent à interagir avec l'agent. Par exemple, *Que dois-je manger ce midi ?*

Son rôle étant unique dans le fonctionnement de l'agent virtuel, la configuration de son comportement est importante. La capacité **None of the above (Aucun des choix ci-dessus)** est souvent déclenchée et de manières pas toujours évidentes. Par exemple :

- Si vous désactivez une autre capacité de base, les énoncés qui déclenchent la capacité désactivée sont réacheminés vers la capacité **None of the above (Aucun des choix ci-dessus)** pour une réponse.
- Si un énoncé ne correspond à aucune des capacités de base activées, il est transmis à la capacité **None of the above (Aucun des choix ci-dessus)** pour une réponse. Si vous fournissez un espace de travail associé avec des capacités personnalisées, l'espace de travail de base et l'espace de travail personnalisé évaluent tous deux l'énoncé pour rechercher une correspondance. Si aucune correspondance n'est trouvée, la réponse associée à la capacité de base **None of the above (Aucun des choix ci-dessus)** est utilisée.
- Vous pouvez configurer la capacité **None of the above (Aucun des choix ci-dessus)** de sorte à avoir un type de réponse **Use your own conversation (Utiliser votre propre conversation)** et à l'associer à un espace de travail avec un dialogue personnalisé. Si aucune intention ne correspond à un énoncé dans l'espace de travail de base, l'énoncé est transmis à la capacité **None of the above (Aucun des choix ci-dessus)**, qui la transmet à l'espace de travail personnalisé pour une réponse.
- Si vous dissociez un espace de travail et que cet espace de travail est associé à la capacité **None of the above (Aucun des choix ci-dessus)**, vous devez effectuer une action pour pouvoir continuer à dissocier l'espace de travail. Toute autre capacité associée à l'espace de travail à dissocier est automatiquement désactivée. Toutefois, la capacité **None of the above (Aucun des choix ci-dessus)** ne pouvant pas être désactivée, vous devez déterminer un comportement de réponse de remplacement. Par exemple, vous pouvez remplacer le type de réponse par **Text (Texte)** et ajouter un message textuel à utiliser dans la réponse.
