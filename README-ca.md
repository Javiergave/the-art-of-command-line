🌍
*[Čeština](README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [English](README.md) ∙ [Español](README-es .md) ∙ [Français](README-fr.md) ∙ [Indonèsia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [ 한국어](README-ko.md) ∙ [polski](README-pl.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский-ru](README-pt.md) .md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁ANTME-zh.md](繁ANTME-zh. )*


# L'art de la línia de comandaments

*Nota: estic planejant revisar-ho i buscar un nou coautor que m'ajudi a ampliar-ho a una guia més completa. Tot i que és molt popular, podria ser més ampli i una mica més profund. Si t'agrada escriure i estàs a prop de ser un expert en aquest material i estàs disposat a considerar ajudar-te, envia'm una nota a josh (0x40) holloway.com. –[jlevy](https://github.com/jlevy), [Holloway](https://www.holloway.com). Gràcies!*

- [Meta](#meta)
- [Funcions bàsiques](#bàsiques)
- [Ús diari](#ús-diari)
- [Processament de fitxers i dades](#processing-files-and-data)
- [Depuració del sistema](#system-debugging)
- [One-liners](#one-liners)
- [Obscure però útil](#obscure-però-útil)
- [només macOS](només #macos)
- [només Windows](només #windows)
- [Més recursos](#more-resources)
- [Avís legal](#exempció de responsabilitat)


![curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d ''' | cowsay -W50](cowsay.png)

La fluïdesa a la línia d'ordres és una habilitat que sovint es descuida o es considera arcana, però millora la vostra flexibilitat i productivitat com a enginyer tant de manera òbvia com subtil. Aquesta és una selecció de notes i consells sobre l'ús de la línia d'ordres que hem trobat útils quan treballem amb Linux. Alguns consells són elementals i alguns són força específics, sofisticats o obscurs. Aquesta pàgina no és llarga, però si podeu utilitzar i recordar tots els elements aquí, en saps moltes coses.

Aquest treball és el resultat de [molts autors i traductors](AUTHORS.md).
Part d'això
[originalment](http://www.quora.com/What-are-some-lesser-known-but-useful-Unix-commands)
[aparegut](http://www.quora.com/What-are-the-most-useful-Swiss-army-knife-one-liners-on-Unix)
a [Quora](http://www.quora.com/What-are-some-time-saving-tips-that-every-Linux-user-should-know),
però des de llavors s'ha traslladat a GitHub, on persones amb més talent que l'autor original han fet nombroses millores.
[**Envieu una pregunta**](https://airtable.com/shrzMhx00YiIVAWJg) si teniu una pregunta relacionada amb la línia d'ordres. [**Si us plau, contribuïu**](/CONTRIBUTING.md) si veieu un error o alguna cosa que podria ser millor!

## Meta

Àmbit:

- Aquesta guia és per a usuaris principiants i experimentats. Els objectius són *amplitud* (tot el que és important), *especificitat* (donar exemples concrets del cas més comú) i *brevetat* (evitar coses que no són essencials o digressions que podeu buscar fàcilment en altres llocs). Cada consell és essencial en alguna situació o estalvia molt temps respecte a alternatives.
- Això està escrit per a Linux, amb l'excepció de les seccions "[només macos](només macos)" i "[només per a Windows](només per a Windows)". Molts dels altres elements s'apliquen o es poden instal·lar en altres Unices o macOS (o fins i tot Cygwin).
- El focus se centra en Bash interactiu, tot i que molts consells s'apliquen a altres shells i als scripts generals de Bash.
- Inclou tant ordres Unix "estàndard" com les que requereixen instal·lacions especials de paquets, sempre que siguin prou importants com per merèixer la seva inclusió.

Notes:

- Per mantenir-ho en una pàgina, el contingut s'inclou implícitament per referència. Sou prou intel·ligent per buscar més detalls en altres llocs un cop conegueu la idea o l'ordre a Google. Utilitzeu `apt`, `yum`, `dnf`, `pacman`, `pip` o `brew` (segons correspongui) per instal·lar programes nous.
- Utilitzeu [Explainshell](http://explainshell.com/) per obtenir un desglossament útil de què fan les ordres, les opcions, les canonades, etc.


## Conceptes bàsics

- Aprendre Bash bàsic. De fet, escriviu `man bash` i, com a mínim, escriviu-ho tot; és bastant fàcil de seguir i no tant llarg. Els shells alternatius poden ser agradables, però Bash és potent i sempre està disponible (aprendre *només* zsh, fish, etc., mentre que tempta el vostre propi ordinador portàtil, us restringeix en moltes situacions, com ara utilitzar servidors existents).

- Apreneu bé almenys un editor de text. L'editor `nano` és un dels més senzills per a l'edició bàsica (obrir, editar, desar, cercar). Tanmateix, per a l'usuari avançat en un terminal de text, no hi ha cap substitut per Vim (`vi`), l'editor difícil d'aprendre però venerable, ràpid i amb totes les funcions. Molta gent també utilitza el clàssic Emacs, especialment per a tasques d'edició més grans. (Per descomptat, és poc probable que qualsevol desenvolupador de programari modern que treballi en un projecte extens utilitzi només un editor basat en text i també hauria d'estar familiaritzat amb els IDE i les eines gràfiques modernes.)

- Recerca de documentació:
   - Saber llegir documentació oficial amb `man` (per als curiosos, `man man` enumera els números de secció, per exemple, 1 és ordres "normals", 5 és fitxers/convencions i 8 són per a l'administració).
