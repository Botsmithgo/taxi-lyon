# Taxi Lyon — Site vitrine (v1)

Site web vitrine pour un service de taxi conventionné CPAM à Lyon. Fichier HTML unique, autonome, sans dépendance.

## 📁 Fichiers

- **`index.html`** — le site complet (HTML + CSS inline + 1 ligne de JS pour l'année du footer)
- **`README.md`** — ce fichier

## 🚀 Ouvrir le site

```bash
open index.html
```

Ou le glisser dans n'importe quel navigateur. Aucun build, aucun serveur, aucune dépendance.

## 🔧 Placeholders à remplacer

Avant de publier, fais un **search & replace** dans `index.html` sur ces 9 chaînes :

| Placeholder | Exemple | Où |
|---|---|---|
| `[NOM_ENTREPRISE]` | `Taxi Dupont Lyon` | title, header, footer, JSON-LD |
| `[NOM_CHAUFFEUR]` | `Mehdi Dupont` | footer, témoignage |
| `[TÉLÉPHONE]` | `04 78 00 00 00` | affichage visible (format français) |
| `[TÉLÉPHONE_INTL]` | `+33478000000` | liens `tel:` (format international, sans espaces) |
| `[EMAIL]` | `contact@taxi-lyon.fr` | liens `mailto:`, formulaire |
| `[WHATSAPP]` | `33612345678` | liens `wa.me/` (sans `+`, sans espaces) |
| `[NUM_LICENCE_TAXI]` | `Licence n° 123 — Préfecture du Rhône` | footer |
| `[ADRESSE]` | `Lyon, Rhône (69)` | contact, footer |
| `[HORAIRES]` | `7j/7 — 24h/24` | contact, footer |

### Commande rapide pour lister les placeholders restants

```bash
grep -oE '\[[A-ZÉÈ_]+\]' index.html | sort -u
```

### Exemple de sed pour remplacer (macOS)

```bash
sed -i '' 's/\[NOM_ENTREPRISE\]/Taxi Dupont Lyon/g' index.html
sed -i '' 's/\[TÉLÉPHONE\]/04 78 00 00 00/g' index.html
sed -i '' 's/\[TÉLÉPHONE_INTL\]/+33478000000/g' index.html
# etc.
```

## 🎨 Design

- **Palette** : bleu profond `#0B3D6F` + cyan `#4FB3E8` + vert santé `#10B981` — ambiance médicale pro & rassurante
- **Typographie** : système (pas de Google Fonts → performance + RGPD friendly)
- **Images** : Unsplash (libres de droits, chargées à la volée)
- **Responsive** : mobile-first, breakpoints à 768px et 900px
- **Accessibilité** : contraste AA, `lang="fr"`, focus visible, `aria-label` partout
- **SEO** : meta description, Open Graph, JSON-LD `TaxiService`, title riche en mots-clés

## 📱 Features mobiles

- **Sticky bottom bar** (<768px) : 3 boutons gros doigts → Appeler · WhatsApp · Devis
- **Menu burger** : 0 JS, pur CSS (checkbox hack)
- **Boutons `tel:` et `wa.me`** : ouvrent directement l'app native

## 📸 Images custom (v1.1 optionnel)

Les URLs Unsplash actuelles donnent un rendu pro instantané. Si tu veux du custom (photos du vrai chauffeur, vrai véhicule) :

1. Remplacer les URLs `images.unsplash.com/...` par des fichiers locaux (`img/hero.jpg`, etc.)
2. Ou générer des visuels avec Gemini / DALL-E / Midjourney sur les thèmes :
   - Hero : intérieur cuir propre d'une berline, éclairage doux
   - Service médical : hôpital bienveillant, mains qui se serrent
   - Longue distance : autoroute française, coucher de soleil
   - Zone : skyline Lyon (Fourvière + Confluence)

## 🔌 Formulaire — brancher un vrai backend (v2)

Le formulaire utilise `action="mailto:[EMAIL]"` en v1 (ouvre le client mail du visiteur). Pas idéal en prod. Options :

1. **Formspree** (gratuit jusqu'à 50/mois) : remplacer `action` par `https://formspree.io/f/XXXX`
2. **Netlify Forms** : ajouter `netlify` à la balise `<form>` et héberger sur Netlify
3. **Web3Forms / Getform** : équivalents Formspree

## 🌐 Mise en ligne

Options simples & gratuites :

| Host | Avantage |
|---|---|
| **Netlify** | Drag & drop du dossier, HTTPS auto, forms inclus |
| **Vercel** | Idem, ultra rapide |
| **GitHub Pages** | Gratuit, custom domain |
| **OVH / o2switch** | Si domaine `.fr` déjà chez un hébergeur FR |

Pour un `.fr` crédible côté France, privilégier OVH ou Gandi + Netlify pour le site.

## 📋 Avant publication (checklist prod)

- [ ] Tous les placeholders remplacés
- [ ] **Mentions légales** rédigées (obligation légale en France)
- [ ] **Politique de confidentialité RGPD** (collecte de données formulaire)
- [ ] Numéro SIRET ou licence taxi vérifié dans le footer
- [ ] Formulaire branché (Formspree ou équivalent)
- [ ] Test des liens `tel:` sur vrai smartphone
- [ ] Test du formulaire → email bien reçu
- [ ] Favicon ajouté (`<link rel="icon">`)
- [ ] Google Business Profile créé pour le SEO local
- [ ] URL du site ajoutée dans le JSON-LD (champ `url`)

## 💡 Idées v2

- Page blog SEO local : "Comment obtenir une prise en charge CPAM à Lyon ?", "Choisir un taxi conventionné"
- Page dédiée par hôpital (HCL, Centre Léon Bérard, etc.) pour le SEO longue traîne
- Version anglaise pour l'aéroport
- Système de réservation en ligne avec calendrier
- Avis Google Business intégrés en direct
- Chat WhatsApp Business
- Zone pros (cabinets médicaux, maisons de retraite) avec formulaire dédié
