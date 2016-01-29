#KITEGURU REPORT
Elias Houttuijn Bloemendaal
11122056

##Inleiding
KITEGURU is een persoonlijke advies gever. Deze op IOS gebaseerde applicatie zal het bepalen van kiten voor iedereen vermakkelijken. De gebruiker zal eerst zijn gear plus gewicht moeten toevoegen:, wetsuits, kites, boots, hood en globes en het eigen gewicht. Bij het persoonlijke account wordt "the gear meter" weer gegeven. Deze view schept een beeld wat voor gear er nodig is bij een bepaalde water temperatuur. Nadat de gebruiker deze gegevens heeft ingevuld, zal de gebruiker de mogelijkheid krijgen om een plaats in de wereld op te zoeken (een plaats waar de user wil gaan kiten).  Wanneer deze zoekactie voltooid is, wordt de opgezochten plaats vertoond op een map en de weersverwachtingen bij die plaats komen dan ook in beeld. Hierna kan de gebruiker een persoonlijk advies van KITEGURU krijgen op basis van zijn ingevoerde gegevens voor het programma. De gebruiker is daarna in staat om een mail met deze gegevens door te sturen naar wie die wil.

Technical design
Er zijn drie belangrijk mappen waar ik op in zal gaan: Frameworks, ViewController, Models.
Deze drie mappen bevatten ongeveer alles van mijn project.

Frameworks helpen bij het configureren van de data, dat op de applicatie word ingevoerd, om het op correct wijze door te sturen naar de PARSE Database.
https://www.youtube.com/playlist?list=PLum6kTc8U8Cibv6tbEGNG5311oV_-PPDf
Kevin Caughman - youtube series.

ViewContollers zijn alle User Interface die direct verbonden zijn aan mijn code. Hier worden allen variabelen gedeclareerd en wordt de interface bepaalt. De IBActions (Deze actions omschrijven de inhoud van de buttons en wat er gebeurd als er op geklikt wordt) worden hier d.m.v functies geholpen.
Dit zijn alle ViewControllers in mijn project:
SignInViewController
SignUpVieController
PersonalAccountViewController
WeaterPredictionsViewController
PersonalRatingViewcontroller
MailViewController

Models, Dit zijn alle files die functies bevatten. Deze functies staan actions in de ViewController bij  om hun actie bij te staan en goed uit te voeren. Deze models helpen bijvoorbeeld bij het transformeren van JSON data naar leesbare data Of het veranderen van data die verkregen word van de PARSE database naar ook leesbare data of leesbare data voor labels en button’s.
Er zijn ook functies omschreven die bepaalde handelingen zeggen over de input van een textfield, bijvoorbeeld waar niet meer dan een bepaald aantal karakters gebruikt mag worden geef anders een error. Deze functies worden aangeroepen in de ViewControllers d.m.v eerst te zeggen wat wat de class naam is en daarna de naam van de functie aan te schrijven.
Dit zijn allen models in mijn project.
BasicFunctions.swift
SignUp.swift
Enums.swift
SignIn.swift
Parsemodel.swift
WeatherService.swift
SwiftyJSON.swift
Weather.swift

De UI van de applicatie heeft dus zoals al verteld verschillen de button’s , labels en textfields die verbonden zijn met functies uit andere classes. Beginnend bij de SignInViewController: deze gebruikt de model signin.swift. die wordt aangeroepen door de classname signin().login . Hier wordt de USER in gelogd. Als er nog geen gebruiker is aangemaakt, wordt dat gedaan in de SignUpViewController. 

Deze SignUpViewController maakt gebruik van twee verschillende models. De enums.swift + de SignUp.swift + parsemodel.swift In de enums file worden de errors beschreven die weer opgeroepen worden in de signup file. De signup wordt d.m.v de class Signup(). (alle functies die in deze file staan) opgeroepen. Dit zal errors geven in het signup scherm. Als er dan een user account aagemaakt is kunnen mensen weer terug naar de signInViewController om vervolgens in te loggen. Dan komt de nieuwe user aan bij de personalAccountViewController.

De personalAccountViewController wordt bij gestaan door de BasicFunctions.swift. Hier zit een class in de heet Functions. Dus het wordt aangeroepen op de manier van Functions().(De functie naam).
Deze functies houden in de gaten dat er geen rare fratsen gebeuren met textfields. als alles mooi gehecked is nadat de user zijn gegevens heeft ingevoerd (dat gecontroleerd is door de basicfunctions.swift file) Is er de mogelijk om de gebruiker naar het volgende scherm te gaan die gelinked is met de WeatherPredictionsViewController.  

De WeatherPredictionsViewController maakt gebruik van drie verschillende swift files: swiftJSON.swift, weatherService.swift en de weather.swift. Op deze swift files wordt ook twee API’s gebruikt. Die in de ViewController hun gegeven tonen. Dit is mogelijk d.m.v. de navigation-search bar. Hier kan de user een plaats invoeren. Deze wordt dus voor 2 verschillende API’s tegelijkertijd gebruikt. De weather API plust mapKit API. Deze drie swift files: swiftyJSON.swift, weatherService.swift en de weather.swift. Zullen de informatie van www.openweathermap.org zo converteren dat er uiteindelijk leesbare data uitkomt die dan verwerkt word in labels van die WeatherPredictionsViewController.

Als de gebruiker de date heeft kunnen op vragen zal de gebruiker verder kunnen gaan d.m.v de advise knop in te tikken. Nu zal PersonalRatingViewConroller inzicht komen. Deze ViewController word weer bijgestaan de BasicFunctions.swift file die data naar een leesbare manier zal converteren. In de PersonalRatingViewConroller zit een rekenmodel ingebouwd die de gebruiker een advies geeft. Deze berekeningen maken ook gebruik van BasicFunctions.swift
De gebruiker kan als het tevreden is met zijn resultaat een mailtje versturen naar zijn vrienden. 

Als de knop naar de mail wordt ingedrukt. zal der ook een functie worden opgeroepen uit BasicFunctions.swift die een screenshot zal maken van het scherm. De gegevens worden ook doorgestuurd d.m.v. de segue functie. Dit was de laatste screen van mijn app.

##Overwonnen Challenges
Bij dit project ben ik tegen aardig wat problemen aangelopen en ik heb dat in mijn ogen allemaal op mijn eigen manier opgelost. Er zijn ook zeker moeilijkheden voorgekomen waar ik geen weet van had. Dit heb ik op mijn eigen manier (niet de gebruikelijkere manier) opgelost. Een voorbeeld hiervan is dat ik een foto wilde toevoegen aan mijn mail als attachment. Uiteindelijk heb ik dit opgelost door het toe te voegen aan de mail in plaats van een attachment. Dit was een kleine challenge. 

Als er chronologisch door de process file gelopen wordt, is  de eerste grote challenge dat ik niet wist wat een API was en hoe ik dit moest linken aan mijn applicatie. Nadat ik uiteindelijk wist wat een API precies was, en hoe ik die data op mijn applicate kon opvragen en bewerken. was mijn eerste en grootste hindernis overwonnen. Het bewerken van deze weather data in de vorm van JSON is mij uiteindelijk gelukt door veel filmpjes te kijken op youtube en uiteindelijk d.m.v en github file over te nemen met de naam swiftJSON.swift . Hierdoor kon ik the weaterpredictions mooi weer geven in mijn view controllers.

De tweede grote challenge was de gegevens van user’s koppelen aan een database zodat er een eigen account aangemaakt kan worden met de persoonlijke gegevens van een gebruiker. In het begin moest ik natuurlijk eerste uitzoeken wat het precies was en hoe te gebruiken was. wanneer ik die kennis had op gedaan kon ik aan de slag.

Nadat iemand zijn eigen account heeft geupdated (dus eigenlijk zijn gear plus gewicht heeft aangepast in de database van parse) kan er een rekenmodel op los worden gelaten die bepaalt of kitesurfen mogelijk is voor de persoonlijke user. Dit koste veel meer tijd dat ik uiteindelijk had verwacht.

De derde Grote challange wat het koppelen van de API van map kit view aan de API van de weatherpredictor. Dus op het moment dat er in mijn navigatie bar word gezocht zullen er 2 Api’s uiteindelijk te werk gaan. 

##Keuze verdediging 
De weather API die ik heb gebruikt, was nog wel een aardig lastige keuze. In het begin wilde ik verschillende gebruiken maar nadat ik mij, logisch, de keuze heb gemaakt dat ik er voor eentje ben gegaan was het die van openweathermap.org. Deze heb ik gekozen boven magic seawead omdat er veel over te vinden was hoe deze data die wordt verkregen van deze website makkelijk en op veel manieren te verwerken is. openweathermap.org was ook makkelijk zonder enige betaling te verkrijgen, Magicseawead deed daar en tegen er veel moeilijker over. Bij MagicSeawead had ik misschien accuratere data kunnen verkrijgen maar dan had ik het pas na de tweede week kunnen toepassen. Omdat ik op dat moment ook nog geen kennis had van API’s was het sowieso de makkelijkere keuzen om voor openweathermap.org te gaan.
Voor de database parse die ik heb gebruikt, was het eerste wikken en wegen voordat ik dat wilde gaan doen. Ik heb getwijfeld tussen SQL site en parse. Parse kon ik meer over vinden dus heb ik daar uiteindelijk voor gekozen.
Bij de MapviewKit was het een makkelijk beslissing omdat Mapkitview al ingebouwd zit in het ontwerpen van applicaties.

#(persoonlijke review - optioneel)
Het project was uiteindelijk voor mij een eye opener op het gebied van programmeren. In dit project heb ik naar mijn idee echt dingen geleerd die ik op mijn eigen manier wilde doen. Zelf uitzoeken en zelf oplossingen vinden. Dingen waar ik geen weet van had Bijvoorbeeld  op welke manier er een app gebouwd wordt, hoeveel tijd sommige dingen in beslag nemen.
Het lijk mij erg leuk om hier mee verder te gaan op het gebied van IOS Programmeren.

