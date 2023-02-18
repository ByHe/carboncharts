
# Om du testar projektet
Glöm då inte efter det att du clonat
```bash
npm install
```
# Om Carbon Charts 
## Installera Carbon Charts

```bash
npm install -D @carbon/charts-svelte d3
```
### Filerna jag gjort
Ligger i katalgen
```bash
src/lib/components
```

### Ändringar
```bash
+page.svelte
```

## Configurera
vite.config.js
```javascript
import { sveltekit } from '@sveltejs/kit/vite';
import { defineConfig } from 'vite';

export default defineConfig({
	plugins: [sveltekit()],
	ssr: {
		noExternal:
			process.env.NODE_ENV === 'production'
				? ['@carbon/charts', 'carbon-components']
				: [],
	}
});
```
Där det nya är
```javascript
	ssr: {
		noExternal:
			process.env.NODE_ENV === 'production'
				? ['@carbon/charts', 'carbon-components']
				: [],
	}
```

## Format på data
### Exempel med en serie
```json
[
      {
         group: "CPU",
         date: "2020-12-10T22:59:15.000Z",
         value: 10,
      },
      {
         group: "CPU",
         date: "2020-12-10T22:59:30.000Z",
         value: 15,
      },
      {
         group: "CPU",
         date: "2020-12-10T22:59:45.000Z",
         value: 7,
      }
]
```
### Exempel med två serier
Serier åtskiljs med namnet till **group:**
```json
[
      {
         group: "CPU",
         date: "2020-12-10T22:59:15.000Z",
         value: 10,
      },
      {
         group: "CPU",
         date: "2020-12-10T22:59:30.000Z",
         value: 15,
      },
      {
         group: "Temp",
         date: "2020-12-10T22:59:15.000Z",
         value: 3,
      },
      {
         group: "Temp",
         date: "2020-12-10T22:59:30.000Z",
         value: 7,
      },

]
```

## Format på x-axel
I Chart.svelte deklarerar jag 
```javascript
let options = ...;
```
Under **timeScale** kan man göra mycket med hur x-axeln skall formateras. Antar att den skall ändras beroende på datan, day, week eller year.
Enklelt då **option** blir ett objekt.

```json
timeScale: {
timeIntervalFormats: {
   hourly: {
      primary: "MMM d, HH:mm",
      secondary: "HH:mm",
   },
},
}
```
## Dokumentation 
[Carbon Charts](https://charts.carbondesignsystem.com/?path=/story/docs--welcome)
