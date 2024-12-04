<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Poursuites d'études et Métiers </title>
    <style>
        
        body {
            font-family: Arial, sans-serif;
            background-color: #eef2f3;
            padding: 20px;
        } 
        .secteur {
            display: inline-block;
            width: 28%; /* Trois colonnes */
            margin-right: 1.5%;
            vertical-align: top;
            background-color: #ffffff; /* Fond blanc */
            border-radius: 8px; /* Coins arrondis */
            box-shadow: 0 4px 8px rgba(0,0,0,0.1); /* Ombre légère */
            padding: 15px; /* Espacement interne */
        }
        .secteur h2 {
            color: #333;
            text-align:center;
            border-bottom: 2px solid #3498db; /* Ligne sous le titre */
            padding-bottom: 10px;
        }

        .metier {
            margin-bottom: 15px; /* Espacement entre les métiers */
        }

        .metier h3 {
            color:#3498db; /* Couleur pour les titres des métiers */
        }
        h1, h2 { color: #333; }
        .container { display: flex; flex-wrap: wrap; }
        .metier { margin: 10px; padding: 10px; border-radius: 5px; cursor: pointer; }
        .formation { width: 45%; margin: 10px; padding: 10px; border-radius: 5px; cursor: pointer; }
        .metier { background-color: #e6f3ff; }
        .formation { background-color: #e6ffe6; }
        .possibilites { display: none; margin-left: 20px; padding: 10px; background-color: #f0f0f0; border-radius: 5px; }
        .sous-formation { margin-top: 10px; padding: 5px; background-color: #fff; border-radius: 3px; }
        body {
    background-color: #f0f8ff;
    font-family: 'Arial', sans-serif;
}
@media (max-width: 1200px) {
    .secteur {
        width: calc(33.33% - 20px); /* Trois colonnes sur écrans moyens */
    }
}

@media (max-width: 900px) {
    .secteur {
        width: calc(50% - 20px); /* Deux colonnes sur écrans plus petits */
    }
}

@media (max-width: 600px) {
    .secteur {
        width: 100%; /* Une seule colonne sur petits écrans */
    }
}
.metier:hover {
    transform: scale(1.02); /* Agrandit légèrement au survol */
    transition: transform 0.3s ease; /* Transition douce */
}
.separator {
    height: 1px;
    background-color: #ccc;
    margin: 10px 0;
}
.metier {
    background-color: #fff; /* Fond blanc */
    border-radius: 8px; /* Coins arrondis */
    box-shadow: 0 4px 8px rgba(0,0,0,0.1); /* Ombre légère */
    padding: 15px; /* Espacement interne */
    margin-bottom: 15px; /* Espacement entre les cartes */
    transition: transform 0.2s; /* Transition douce */
}

.metier:hover {
    transform: scale(1.02); /* Agrandissement au survol */
}
h1, h2 {
    color: #2c3e50;
    text-align: center;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
}

.metier, .formation {
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
}

.metier:hover, .formation:hover {
    transform: translateY(-5px);
}

.metier h3, .formation h3 {
    background-color: #3498db;
    color: white;
    padding: 10px;
    margin: 0;
    border-radius: 5px 5px 0 0;
}

.possibilites {
    border-top: 1px solid #bdc3c7;
    margin-top: 10px;
    padding-top: 10px;
}

.sous-formation {
    background-color: #ecf0f1;
    margin: 5px 0;
    padding: 10px;
    border-radius: 3px;
}
    </style>
</head>
<body>
    <h1>Poursuites d'études et Métiers</h1>
    <div style="text-align: center; margin: 20px 0;">
        <a href="https://saintecatherinesti2d.glide.page" target="_blank" style="font-size: 18px; color: #3498db; text-decoration: none;">
            Accéder à l'application Sainte Catherine STI2D en complément pour voir les projets réalisés en I2D et Energie ainsi qu'avoir accès aux documents relatifs à la filière<BR>
        </a>
    </div>
    <h2>Métiers</h2>
    <div class="container" id="metiers-container"></div>

    <h2>Formations (double clic pour entrer dans les caractéristiques de la formation) </h2>
    <div class="container" id="formations-container"></div>

    <script>
    const metiersParSecteur = {
        "Énergie": [
        { titre: "Technicien en énergies renouvelables", description: "Installe et maintient des systèmes d'énergie renouvelable.", parcours: "BTS FEE → Licence pro énergies renouvelables → Formation continue" },
        { titre: "Ingénieur environnement", description: "Développe des solutions pour réduire l'impact environnemental des activités humaines.", parcours: "BUT HSE → École d'ingénieurs spécialisée en environnement → Stage dans un bureau d'études environnementales" },
        { titre: "Ingénieur en efficacité énergétique", description: "Optimise la consommation énergétique des bâtiments ou industries.", parcours: "BUT GTE → École d'ingénieurs en énergie → Stage dans un bureau d'études thermiques" },
        { titre: "Ingénieur en géothermie", description: "Conçoit et met en œuvre des systèmes de chauffage géothermique.", parcours: "BUT GTE → École d'ingénieurs en géologie → Stage dans une entreprise de forage géothermique" },
        // Nouveaux métiers ajoutés
        { titre:"Ingénieur en énergies renouvelables", description:"Conçoit et développe des systèmes utilisant des sources d'énergie renouvelable.", parcours:"Bac STI2D→École d'ingénieurs spécialisée en énergies renouvelables→Stage en entreprise."},
        { titre:"Technicien en efficacité énergétique", description:"Évalue et améliore l'efficacité énergétiquedes bâtiments et de ssystèmes industriels.", parcours:"BTS FEE→Licence pro en efficacité énergétique → Formation continue."},
        { titre:"Ingénieur en hydraulique", description:"Conçoit et gère des systèmes hydrauliques pour l'énergie et l'eau.", parcours:"BUT Génie hydraulique → École d'ingénieurs spécialisée en hydraulique → Stage dans un bureau d'études."},
        { titre:"Technicien en maintenance énergétique", description:"Assure lamaintenance desinstallations énergétiquesdanslesbâtiments.", parcours:"BTS Maintenance dessystèmes→Licenceproen gestion del'énergie→Expérienceenentreprise."},
        { titre:"Ingénieur en stockage d'énergie", description:"Développe des solutions de stockage pour optimiser l'utilisation des énergies renouvelables.", parcours:"Prépa MP→École d'ingénieurs spécialisée en énergie → Stage dans une entreprise de stockage."},
        { titre:"Consultant en transition énergétique", description:"Accompagne les entreprises dans leur transition vers des pratiques énergétiques durables.", parcours:"Licence en sciences de l'environnement → Master en transition énergétique → Stage dans un cabinet de conseil."},
        { titre:"Ingénieur en réseaux électriques intelligents (Smart Grids)", description:"Conçoit et optimise des réseaux électriques pour intégrer les énergies renouvelables.", parcours:"Bac STI2D → École d'ingénieurs spécialisée en réseaux électriques → Stageenentreprise."},
        { titre:"Technicien de laboratoire en énergies renouvelables", description:"Effectue des tests et analyses sur les technologies d'énergie renouvelable.", parcours:"BTS Métiers de la chimie → Licence pro enénergies renouvelables → Formation continue."},
        { titre:"Ingénieur en biogaz", description:"Développe et gère des projets de production de biogaz à partir de déchets organiques.", parcours:"BUT Génie biologique →École d'ingénieurs spécialisée en biogaz → Stagedansuneentreprisedetraitementdesdéchets."},
        { titre:"Responsablede projet énergie", description:"Gère des projets liés à la production et à la gestion del'énergie.", parcours:"Bac STI2D → École d'ingénieurs spécialisée en énergie → Expérience dans la gestion de projets."}
    ],
    "Génie Civil": [
        { titre: "Ingénieur en génie civil", description: "Conçoit et dirige des projets d'infrastructure et de construction.", parcours: "BUT Génie civil → École d'ingénieurs en génie civil → Stage dans un bureau d'études." },
        { titre: "Conducteur de travaux", description: "Supervise et coordonne les chantiers de construction.", parcours: "BTS Bâtiment → Licence pro conducteur de travaux → Expérience sur chantier." },
        { titre: "Architecte", description: "Conçoit des bâtiments et supervise leur construction.", parcours: "Licence en architecture → Master en architecture → Stage en cabinet d'architecture." },
        { titre: "Urbaniste", description: "Planifie et organise le développement des zones urbaines.", parcours: "Licence en géographie → Master en urbanisme → Stage dans une collectivité territoriale." },
        { titre: "Ingénieur structures", description: "Analyse et conçoit des structures résistantes pour les bâtiments.", parcours: "Prépa PCSI → École d'ingénieurs spécialisée en génie civil → Stage dans un bureau d'études." },
        { titre: "Technicien en géomètre", description: "Réalise des relevés topographiques et des plans pour l'aménagement du territoire.", parcours: "BTS Géomètre-topographe → Licence pro en aménagement du territoire → Stage dans un cabinet d'urbanisme." },
        { titre: "Ingénieur en hydraulique", description: "Conçoit et gère des systèmes hydrauliques pour l'énergie et l'eau.", parcours: "BUT Génie hydraulique → École d'ingénieurs spécialisée en hydraulique → Stage dans un bureau d'études." },
        { titre: "Technicien de laboratoire de matériaux", description: "Effectue des tests sur les matériaux utilisés dans la construction.", parcours: "BTS Métiers de la chimie → Licence pro en matériaux de construction → Formation continue." },
        { titre: "Ingénieur en infrastructures routières", description: "Conçoit et supervise la construction de routes et d'infrastructures de transport.", parcours:"Bac STI2D→École d'ingénieurs spécialiséeen infrastructures→Stagechezun constructeur routier."},
        { titre:"Responsable qualité dans le bâtiment", description:"Assure la conformité des travaux aux normes de qualité et de sécurité.", parcours:"BTS Bâtiment→Licence pro en gestion de la qualité dans le bâtiment→Expérience sur chantier."},
        { titre:"Ingénieur en infrastructures routières", description:"Conçoit et supervise la construction de routes et d'infrastructures de transport.", parcours:"Bac STI2D→École d'ingénieurs spécialiséeen infrastructures→Stagechezun constructeur routier."},
        { titre:"Technicien en géotechnique", description:"Étudie les caractéristiques des sols pour les projets de construction.", parcours:"BTS Géotechnique→Licence pro en géotechnique→Stage dans un bureau d'études."},
        { titre:"Ingénieur en matériaux de construction", description:"Recherche et développe de nouveaux matériaux pour la construction.", parcours:"BUT Génie des matériaux→École d'ingénieurs spécialiséeen matériaux→Stage dans une entreprise de construction."},
        { titre:"Chef de projet en génie civil", description:"Gère des projets de construction, coordonne les équipes et s'assure du respect des délais et budgets.", parcours:"Bac STI2D→École d'ingénieurs spécialiséeen génie civil→Expérienceen gestionde projet."},
        { titre:"Ingénieur en hydraulique urbaine", description:"Conçoit des systèmes de gestion des eaux pluviales et des réseaux d'assainissement.", parcours:"BUT Génie hydraulique→École d'ingénieurs spécialiséeen hydraulique→Stage dans un bureau d'études."}
    ],
    "Informatique": [
        { titre: "Développeur web", description: "Crée et maintient des sites et applications web.", parcours: "BUT MMI → Licence pro en développement web → Projets personnels et stages" },
        { titre: "Ingénieur logiciel", description: "Conçoit et développe des logiciels complexes.", parcours: "Prépa MP2I → École d'ingénieurs en informatique → Stage dans une entreprise tech" },
        { titre: "Data Scientist", description: "Analyse des données pour extraire des informations utiles.", parcours: "Licence en mathématiques → Master en science des données → Projets personnels en IA" },
        { titre: "Ingénieur en cybersécurité", description: "Protège les systèmes informatiques contre les cyber attaques.", parcours: "BUT Informatique → École d'ingénieurs spécialisée en sécurité → Certifications en cybersécurité" },
        { titre:"Ingénieuren systèmesd'information", description:"Conçoit et gère des systèmes d'information pour les entreprises.", parcours:"Bac STI2D → École d'ingénieurs en systèmes d'information → Stage dans une entreprise."},
        { titre:"Analystede données", description:"Analyse les données pour aider à la prise de décision stratégiques.", parcours:"Bac STI2D → Licence en statistiques → Master en data science."},
        { titre:"Développeur mobile", description:"Crée des applications pour smartphones et tablettes.", parcours:"Bac STI2D → BUT MMI → Licence pro en developpement mobile."},
        { titre:"Ingénieuren intelligenceartificielle", description:"Développedesalgorithmesetdessystèmesbasés surl'IA.", parcours:"Bac STI2D→École d'ingénieurs spécialisée en IA → Stage dans un laboratoire de research."},
        { titre:"Technicien supportinformatique", description:"Assure le support technique et la maintenance des systèmes informatiques.", parcours:"BTS SIO → Expérience en entreprise."}
    ]
};
        const formations = [
        {
        titre: "BTS",
        description: "Brevet de Technicien Supérieur, formation professionnelle en 2 ans après le baccalauréat.",
        sousFormations: [
        { 
        titre: "BTS Finitions, aménagement des bâtiments", 
        description: "Ce BTS forme des spécialistes en finition du bâtiment. Les diplômés sont capables de gérer des chantiers, d'assurer le contrôle qualité, et de travailler sur l'aménagement intérieur et extérieur des bâtiments.Parcours Bac STI2D → BTS Finitions → Licence pro en aménagement du bâtiment" 
        },
        { 
        titre: "BTS Bâtiment", 
        description: "Ce BTS prépare à la gestion technique et au suivi de chantiers de construction. Les étudiants apprennent à coordonner les travaux, de la conception à la réalisation, en respectant les normes de sécurité et environnementales.Parcours Bac STI2D → BTS Bâtiment → Licence pro conducteur de travaux" 
        },
        { 
        titre: "BTS Systèmes constructifs bois et habitat", 
        description: "Spécialisé dans la conception et la réalisation de structures en bois pour le bâtiment, ce BTS forme des experts en charpente et couverture.Parcours Bac STI2D → BTS SCBH → Licence pro en construction durable" 
        },
        { 
        titre: "BTS Conception et réalisation de systèmes automatiques", 
        description: "Ce BTS forme des spécialistes en conception et réalisation de systèmes automatisés pour l'industrie et les services.Parcours Bac STI2D → BTS CRSA → Licence pro en automatisation" 
        },
        { 
        titre: "BTS Contrôle industriel et régulation automatique", 
        description: "Centré sur la gestion et l'optimisation des processus industriels automatisés, ce BTS prépare les étudiants à travailler sur des systèmes de contrôle et de régulation dans divers secteurs industriels.Parcours Bac STI2D → BTS CIRA → Licence pro en contrôle industriel" 
        },
        { 
        titre: "BTS Métiers de la chimie", 
        description: "Formation en chimie appliquée, analyse et contrôle qualité. Les étudiants acquièrent des compétences en synthèse organique, chimie analytique et procédés industriels.Parcours Bac STI2D → BTS Métiers de la chimie → Licence pro en chimie appliquée" 
        },
        { 
        titre: "BTS Biotechnologies", 
        description: "Étude des systèmes biologiques et de leurs applications. Les étudiants se spécialisent dans des domaines tels que la biochimie, la microbiologie ou les biotechnologies.Parcours Bac STI2D → BTS Biotechnologies → Licence pro en biotechnologies industrielles" 
        },
        { 
        titre: "BTS Systèmes Numériques", 
        description: "Formation sur les systèmes numériques et les technologies de l'information.Parcours Bac STI2D → BTS Systèmes Numériques → Licence pro en informatique." 
        },
        { 
        titre: "BTS Électrotechnique", 
        description: "Formation sur la conception et la maintenance des systèmes électriques et électroniques.Parcours Bac STI2D → BTS Électrotechnique → Licence pro en énergies renouvelables." 
        },
        { 
        titre: "BTS Gestion et Maîtrise de l'Eau", 
        description: "Prépare à la gestion des ressources en eau et à l'assainissement.Parcours Bac STI2D → BTS Gestion et Maîtrise de l'Eau → Licence pro en gestion des ressources hydriques." 
        },
        { 
        titre: "BTS Maintenance des Systèmes", 
        description: "Formation sur la maintenance des équipements industriels.Parcours Bac STI2D → BTS Maintenance des Systèmes → Licence pro en maintenance industrielle."  
        },
        {  
        titre:"BTS Informatique et Réseaux pour l'Industrie et les Services Techniques (IRIS)",  
        description:"Formation sur les réseaux informatiques et les systèmes d'information.Parcours Bac STI2D→BTS IRIS→Licenceproenréseauxinformatiques."  
        },  
        {  
        titre:"BTS Design Graphique",  
        description:"Prépare à la création visuelle pour divers supports numériques et imprimés.Parcours Bac STI2D→BTSDG→Licenceproencommunicationvisuelle."  
        },  
        {  
        titre:"BTS Techniques de Commercialisation",  
        description:"Prépare aux métiers du commerce et du marketing. Parcours Bac STI2D→BTSTC→Licenceproenmarketing."  
        },  
        {  
        titre:"BTS Négociationet Digitalisationde la RelationClient (NDRC)",  
        description:"Formation sur la relation client dans un environnement digitalisé. Parcours Bac STI2D→BTSDRC→Licenceproencommerce digital."  
        },  
        {  
        titre:"BTS Métiers du Multimédia et de l'Internet (MMI)",  
        description:"Formation surla création de contenus multimédias pour le web.Parcours Bac STI2D→BTMMI→Licenceproenmétiersdunumerique."  
        },  
        {   
        titre:"BTS Animation3Det EffetsSpéciaux",   
        description:"Prépare aux métiers de l'animation 3D pourle cinéma,les jeux vidéo,etc. Parcours Bac STI2D→BTSA3DE→Licenceproenanimationnumérique."   
        }
        ]
},
            {
        titre: "Licences et Licences Professionnelles",
        description: "Formations universitaires de 3 ans (licence) ou 1 an après un bac+2 (licence pro) préparant à divers domaines professionnels.",
        sousFormations: [
            { titre: "Licence Pro Gestion de Production", description: "Forme des professionnels capables de gérer et optimiser les processus de production dans l'industrie. Parcours : BTS CIRA → Licence Pro Gestion de Production → Expérience en industrie" },
            { titre: "Licence Pro Développement Web", description: "Prépare les étudiants à créer et maintenir des sites et applications web modernes. Parcours : BUT MMI → Licence Pro Développement Web → Projets personnels et stages" },
            { titre: "Licence Pro Énergies Renouvelables", description: "Spécialise les étudiants dans l'installation et la maintenance de systèmes d'énergie renouvelable. Parcours : BTS FEE → Licence Pro Énergies Renouvelables → Formation continue en nouvelles technologies" },
            { titre: "Licence Pro Maintenance Biomédicale", description: "Forme des techniciens pour la maintenance des équipements médicaux dans les hôpitaux. Parcours : BTS Systèmes Numériques → Licence Pro Maintenance Biomédicale → Formation continue" },
            { titre: "Licence Informatique", description: "Donne aux étudiants les compétences nécessaires pour concevoir et développer des logiciels complexes. Parcours : Bac S ou STI2D → Licence Informatique → Stage dans une entreprise tech" },
            { titre: "Licence Génie Civil", description: "Forme des ingénieurs capables de concevoir et diriger des projets d'infrastructure. Parcours : Bac S ou STI2D → Licence Génie Civil → Stage dans un bureau d'études" },
            { titre: "Licence Pro Conduite de Travaux", description: "Prépare à la supervision et coordination des chantiers de construction. Parcours : BTS Bâtiment → Licence Pro Conduite de Travaux → Expérience sur chantier" },
            { titre: "Licence Sciences de l'Environnement", description: "Prépare les étudiants à développer des solutions pour réduire l'impact environnemental. Parcours : Bac S → Licence Sciences de l'Environnement → Stage dans un bureau d'études" }
                ]
        },
            {
        titre: "BUT",
        description: "Bachelor Universitaire de Technologie, formation professionnalisante en 3 ans après le baccalauréat.",
        sousFormations: [
            { titre: "BUT Génie chimique - génie des procédés", description: "Formation sur les procédés de transformation de la matière et de l'énergie. Les étudiants apprennent à concevoir et optimiser des installations industrielles." },
            { titre: "BUT Génie civil - construction durable", description: "Étude des techniques de construction et de gestion de projets dans le bâtiment et les travaux publics, avec un focus sur le développement durable." },
            { titre: "BUT Génie électrique et informatique industrielle", description: "Formation en électronique, électrotechnique et automatisme. Les étudiants développent des compétences en conception de systèmes électriques et en programmation industrielle." },
            { titre: "BUT Informatique", description: "Étude des technologies de l'information et de la programmation. Les étudiants développent des compétences en développement logiciel, bases de données et réseaux." },
            { titre: "BUT Mesures physiques", description: "Formation en métrologie et instrumentation. Les étudiants apprennent à effectuer des mesures précises dans divers domaines scientifiques et industriels." }
                ]
        },
            {
                titre: "Classes préparatoires aux grandes écoles (CPGE)",
                description: "Formation intensive de 2 ans préparant aux concours des grandes écoles d'ingénieurs.",
                sousFormations: [
                    { titre: "MPSI (Mathématiques, Physique et Sciences de l'Ingénieur)", description: "Cette prépa met l'accent sur les mathématiques et la physique, avec une approche abstraite. Elle prépare aux concours des écoles d'ingénieurs les plus sélectives." },
                    { titre: "PCSI (Physique, Chimie et Sciences de l'Ingénieur)", description: "Cette filière accorde une place importante à la chimie et aux sciences de l'ingénieur, en plus des mathématiques et de la physique. Elle offre une formation équilibrée et ouvre à de nombreuses écoles d'ingénieurs." },
                    { titre: "PTSI (Physique, Technologie et Sciences de l'Ingénieur)", description: "Cette prépa propose une formation de haut niveau en sciences industrielles, en lien avec des problèmes concrets. Elle est particulièrement adaptée aux élèves intéressés par les applications pratiques des sciences." },
                    { titre: "MP2I (Mathématiques, Physique, Ingénierie et Informatique)", description: "Nouvelle filière qui met l'accent sur l'informatique, en plus des mathématiques et de la physique. Elle s'adresse aux élèves passionnés par la programmation et l'algorithmique." },
                    { titre: "TSI (Technologie et Sciences Industrielles)", description: "Réservée aux bacheliers STI2D et STL, cette prépa vise l'analyse de systèmes complexes et la mise en œuvre de solutions technologiques. Elle prépare aux concours d'écoles d'ingénieurs adaptés à ce profil." }
                ]
            }
        ];
                
        function creerElement(item, type) {
            const div = document.createElement('div');
            div.className = type;
            div.innerHTML = `<h3>${item.titre}</h3><p>${item.description}</p>`;
            
            const possibilites = document.createElement('div');
            possibilites.className = 'possibilites';
            
            if (type === 'formation' && item.sousFormations) {
                item.sousFormations.forEach(sousFormation => {
                    const sousDiv = document.createElement('div');
                    sousDiv.className = 'sous-formation';
                    sousDiv.innerHTML = `<h4>${sousFormation.titre}</h4><p>${sousFormation.description}</p>`;
                    possibilites.appendChild(sousDiv);
                });
            } else if (type === 'metier') {
                possibilites.innerHTML = `<p><strong>Parcours possible :</strong> ${item.parcours}</p>`;
            }
            
            div.addEventListener('click', () => {
                possibilites.style.display = possibilites.style.display === 'none' ? 'block' : 'none';
            });
            
            div.appendChild(possibilites);
            return div;
        }

// Fonction pour afficher les métiers par secteur
function afficherMetiersParSecteur() {
    const container = document.getElementById('metiers-container');
    container.innerHTML = ''; // Vide le conteneur

    for (const [secteur, listeMetiers] of Object.entries(metiersParSecteur)) {
        const secteurDiv = document.createElement('div');
        secteurDiv.className = 'secteur';
        
        // Ajout du clic pour afficher ou masquer les métiers
        secteurDiv.innerHTML = `<h2 onclick="toggleSecteur(this)">${secteur}</h2>`;
        
        const metiersListDiv = document.createElement('div');
        
        listeMetiers.forEach(metier => {
            const metierDiv = document.createElement('div');
            metierDiv.className = 'metier';
            metierDiv.innerHTML = `
                <h3>${metier.titre}</h3>
                <p>${metier.description}</p>
                <p><strong>Parcours :</strong> ${metier.parcours}</p>
            `;
            metiersListDiv.appendChild(metierDiv);
            
            // Ajout du séparateur
            const separator = document.createElement('div');
            separator.className = 'separator';
            separator.style.height = '1px';
            separator.style.backgroundColor = '#ccc';
            separator.style.margin = '10px 0';
            metiersListDiv.appendChild(separator);
        });

        metiersListDiv.style.display = 'none'; // Masquer la liste au départ
        secteurDiv.appendChild(metiersListDiv);
        
        container.appendChild(secteurDiv);
    }
}

// Fonction pour basculer l'affichage du secteur
function toggleSecteur(element) {
    const nextSibling = element.nextElementSibling;
    if (nextSibling.style.display === 'none') {
        nextSibling.style.display = 'block';
    } else {
        nextSibling.style.display = 'none';
    }
}

// Appeler cette fonction pour afficher les métiers triés par secteur
afficherMetiersParSecteur();

        const formationsContainer = document.getElementById('formations-container');
        formations.forEach(formation => formationsContainer.appendChild(creerElement(formation, 'formation')));
    </script>
</body>
</html>
