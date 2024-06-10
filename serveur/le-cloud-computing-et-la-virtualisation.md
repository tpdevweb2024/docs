# Le cloud computing et la virtualisation

## La virtualisation

La **virtualisation** consiste à créer des versions virtuelles de ressources physiques, telles que des serveurs, des périphériques de stockage. Cela permet de séparer les ressources matérielles de l'environnement d'exécution, offrant une utilisation plus efficace des ressources physiques.

**les avantages :**&#x20;

**Isolation** : Chaque machine virtuelle fonctionne de manière indépendante, ce qui peut améliorer la sécurité et la gestion des applications.

**Optimisation des ressources**: Meilleure utilisation des ressources physiques par la consolidation de serveurs. ( La consolidation des serveurs consiste à rentabilisé les serveurs physique, réduisant les coûts ainsi qu’en optimisant l’utilisation des serveurs existants, il limite la consommation d’énergie. )



## **Le Cloud Computing**

Le cloud computing fait référence à la mise à disposition de ressources informatiques (comme le stockage, les serveurs, les bases de données, les réseaux, les logiciels, etc.) sur internet. Cette approche permet une grande flexibilité, une mise à l'échelle facile et un paiement selon l'utilisation, ce qui peut réduire les coûts d'infrastructure.

**les avantages :**

**Elasticité** : Capacité à étendre ou réduire les ressources selon la demande, sans intervention manuelle.

**Tarification à l'usage** : Paiement basé sur les ressources consommées.

**Accessibilité** : Accès aux données et applications de n'importe où via internet.

### **les différents types de cloud**

Le cloud computing se révèle être une évolution naturelle de la virtualisation, proposant la mise à disposition de ressources informatiques via internet. Voici les principaux types de cloud :

#### **Cloud public**

Les services sont offerts sur Internet par des fournisseurs tiers et sont accessibles à tous. Ces services sont généralement facturés à l'usage.

AWS / azure / GCP / Scaleway / OVH

#### **Cloud privé**

Un cloud exclusivement utilisé par une seule organisation. Il peut être géré en interne ou par un tiers, et hébergé de manière externe ou sur le site de l'organisation.

Cloudstack / Openstack / Opennebula ( “comme un client légé” )

#### **Cloud hybride**

Combine éléments de cloud public et privé, offrant plus de flexibilité et d'options de déploiement. Les organisations peuvent maintenir des applications critiques en interne tout en utilisant le cloud public pour des besoins évolutifs.





### **Les services Iaas, Paas, Saas.**

#### **IaaS (Infrastructure as a Service)**

IaaS fournit aux utilisateurs un accès à des ressources informatiques telles que des serveurs virtuels, le stockage et les réseaux. Les entreprises peuvent louer ces ressources en fonction de leurs besoins, offrant une alternative flexible et évolutive à l'achat et à la maintenance de matériel physique. Par exemple : Permet de déployer des VM.

**IaaS :** Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform

#### **PaaS (Platform as a Service)**

PaaS offre aux développeurs une plateforme et un environnement pour développer, tester, déployer et gérer des applications sans se soucier de la gestion de l'infrastructure sous-jacente. Cela facilite le processus de développement et permet aux développeurs de se concentrer sur la création de logiciels.

**PaaS :** Heroku, Vercel, Google App Engine, Red Hat OpenShift

#### **SaaS (Software as a Service)**

SaaS permet aux utilisateurs d'accéder à des applications basées sur le cloud via Internet, éliminant la nécessité d'installer et d'exécuter des logiciels sur des ordinateurs individuels. Avec SaaS, les fournisseurs de services maintiennent l'infrastructure et les plateformes logicielles, simplifiant la maintenance et le support pour les clients.

**SaaS :** Salesforce, Google Workspace, Microsoft Office 365, application créer par des devs 🙂

### **En savoir plus**

[https://www.redhat.com/fr/topics/cloud-computing/public-cloud-vs-private-cloud-and-hybrid-cloud](https://www.redhat.com/fr/topics/cloud-computing/public-cloud-vs-private-cloud-and-hybrid-cloud)
