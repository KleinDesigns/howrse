<script setup>
import {ref} from 'vue'

// All colors with index
const horseColors = { "Apfelschimmel": 33, "Apfelschimmel mit Tobiano-Scheckung": 56, "Braun": 4, "Brauner": 26, "Brauner Leopard": 86, "Brauner mit Overo-Scheckung": 77, "Brauner mit Tobiano-Scheckung": 54, "Brauner mit Tovero-Scheckung": 82, "Braunfalben": 59, "Braunschecke": 48, "Cremello": 31, "Cremello mit Tobiano-Scheckung": 70, "Dunkelbrauner": 30, "Dunkelbrauner mit Overo-Scheckung\t": 78, "Dunkelbrauner mit Tobiano-Scheckung": 55, "Dunkelbrauner mit Tovero-Scheckung\t": 83, "Dunkelfuchs": 27, "Dunkelfuchs mit Overo-Scheckung\t": 76, "Dunkelfuchs mit Tobiano-Scheckung": 53, "Dunkelfuchs mit Tovero-Scheckung": 81, "Dunkelfuchs mit heller Mähne": 28, "Dunkelfuchsschecke": 74, "Falb-Schecke\t": 49, "Falbe": 7, "Falbe mit Overo-Scheckung\t": 69, "Falbe mit Tobiano-Scheckung": 65, "Forellenschimmel": 35, "Fuchs": 2, "Fuchs mit Tobiano-Scheckung": 52, "Fuchs mit Tovero-Scheckung\t": 80, "Fuchs mit heller Mähne": 29, "Fuchsschecke": 47, "Gelbfalben": 63, "Graufalben": 60, "Hellfalben": 61, "Hellgrau": 32, "Leicht gefleckter Brauner": 88, "Leicht gefleckter Rotfuchs": 87, "Mausgrau": 34, "Mausgrauer mit Tobiano-Scheckung": 71, "Overo-Fuchsschecke": 67, "Palomino": 16, "Palomino mit Overo-Scheckung\t": 79, "Palomino mit Tobiano-Scheckung": 58, "Palomino mit Tovero-Scheckung": 85, "Palomino-Schecke": 51, "Rappe": 3, "Rappe mit Overo-Scheckung": 66, "Rappe mit Tobiano-Scheckung": 57, "Rappe mit Tovero-Scheckung\t": 84, "Rappschecke": 50, "Roan": 12, "Rotbrauner": 5, "Rotbrauner mit Overo-Scheckung\t": 68, "Rotbrauner mit Tobiano-Scheckung": 64, "Rotfalben": 62, "Rotschecke": 75, "Schabracken-Falbe\t": 38, "Schabrackenbrauner": 37, "Schabrackendunkelfuchs": 72, "Schabrackenfuchs": 36, "Schabrackenpalomino": 40, "Schabrackenrappe": 39, "Schabrackenrotbrauner": 73, "Schimmel": 1, "Strawberry Roan": 10, "Wenige schwarze Flecken\t": 41, "braune Schneeflocke\t": 45, "fuchsfarbene Schneeflocke": 44, "fuchsfarbener Leopard": 42, "schwarze Schneeflocke\t": 46, "schwarzer Leopard": 43   };
 
// Order horseColors
const colors = Object.keys(horseColors).sort().reduce(
  (obj, key) => { 
    obj[key] = horseColors[key]; 
    return obj;
  }, 
  {}
);

// All breeds with index and available colors
const breeds = { 
  "Achal-Tekkiner": {
    "index" : 81,
    "colors": [33,26,31,27,28,7,2,29,32,34,16,3,12,5,10] 
  }, 
  "Amerikanischer Traber": {
    "index": 87,
    "colors": [33,26,30,27,28,7,2,29,32,3,12,5,10]
	}, 
  "Andalusier": {
    "index": 48,
    "colors": [33,26,31, 30,27,28,7,2,29,32,34,16,3,5] 
	}, 
  "Appaloosa": {
    "index": 72,
    "colors": [40,41,42,43,44,45,46,47,48,49,50,51,38,37,3,36,39]
	}, 
  "Araber": {
    "index": 43,
    "colors": [33, 26, 30, 27, 28, 7, 35, 2, 29, 32, 34, 3, 12, 5, 10]
	}, 
  "Argentinischer Criollo": {
    "index": 79,
    "colors": [5, 33, 26, 54, 82, 48, 31, 30, 27, 28, 7, 2, 52, 29, 32, 34, 16, 3, 57, 50, 12]
	}, 
  "Berber": {
    "index": 61,
    "colors": [5, 33, 26, 30, 27, 7, 35, 2, 29, 32, 34, 3]
	}, 
  "Brumby": {
    "index": 62,
    "colors": [10, 33, 26, 31, 30, 27, 7, 35, 2, 29, 32, 34, 16, 3, 12, 5]
	}, 
  "Carmargue-Pferd": {
    "index": 94,
    "colors": [33,35,32,3]
	}, 
  "Curly Horse": {
    "index": 77,
    "colors": [33, 56, 26, 54, 27, 53, 28, 7, 65, 2, 52, 29, 34, 71, 16, 58, 3, 57, 5, 64]
	}, 
  "Deutsches Reitpferd": {
    "index": 46,
    "colors": [33, 26, 30, 7, 2, 32, 34, 3, 12, 5, 10]
	}, 
  "Don-Pferd": {
    "index": 59,
    "colors": [5, 33, 26, 30, 27, 28, 7, 2, 29, 32, 3]
	}, 
  "Englisches Vollblut": {
    "index": 71,
    "colors": [33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Finne": {
    "index": 95,
    "colors": [26,27,28,2,29,3]
	}, 
  "Französischer Traber": {
    "index": 84,
    "colors":[33, 26, 30, 27, 2, 29, 3, 5]
	}, 
  "Friese": {
    "index": 53,
    "colors": [3]
	}, 
  "Hackney": {
    "index": 93,
    "colors": [33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 3, 12, 5, 10]
	}, 
  "Hannoveraner": {
    "index": 45,
    "colors": [ 10, 33, 26, 30, 27, 7, 2, 29, 32, 34, 3, 12, 5]
	}, 
  "Holsteiner": {
    "index": 49,
    "colors": [ 5, 33, 26, 30, 27, 2, 29, 32, 3]
	}, 
  "Irisches Sportpferd": {
    "index": 73,
    "colors":[ 10, 33, 26, 31, 30, 27, 28, 7, 35, 2, 29, 32, 34, 16, 3, 12, 5]
	}, 
  "Isländer": {
    "index": 56,
    "colors": [ 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Knabstrupper": {
    "index": 76,
    "colors": [ 33, 26, 86, 48, 2, 47, 88, 87, 3, 50, 12, 37, 36, 39, 41, 45, 44, 42, 46, 43]
	}, 
  "Lipizzaner": {
    "index": 42,
    "colors": [ 5, 33, 26, 30, 27, 35, 2, 32, 3]
	}, 
  "Lusitano": {
    "index": 68,
    "colors": [ 5, 33, 26, 31, 30, 27, 7, 2, 32, 16, 3]
	}, 
  "Mangalarga Marchador": {
    "index": 97,
    "colors": [ 33, 56, 26, 54, 7, 65, 35, 2, 52, 32, 34, 16, 3, 57, 12, 10]
	}, 
  "Marwari": {
    "index": 63,
    "colors": [ 64, 33, 26, 31, 70, 30, 27, 53, 28, 7, 69, 65, 2, 52, 29, 32, 34, 71, 67, 16, 3, 66, 57, 5, 68]
	}, 
  "Morgan": {
    "index": 64,
    "colors": [ 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Mustang": {
    "index": 58,
    "colors": [ 33, 26, 31, 30, 27, 28, 74, 49, 7, 2, 29, 47, 32, 34, 16, 3, 50, 12, 5, 75, 38, 72, 36, 39, 73, 10, 41]
	}, 
  "Niederländisches Warmblut": {
    "index": 80,
    "colors": [ 5, 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12]
	}, 
  "Nokota": {
    "index": 75,
    "colors": [ 12, 26, 77, 30, 78, 2, 67, 3, 66]
	}, 
  "Oldenburger": {
    "index": 47,
    "colors": [33,26,30,27,2,29,32,3,12,5,10]
	}, 
  "Orlow-Traber": {
    "index": 67,
    "colors": [33,26,30,27,35,2,29,32,34,3,5]
	}, 
  "Paint Horse": {
    "index": 54,
    "colors":[ 56, 77, 54, 82, 78, 55, 83, 76, 53, 81, 69, 65, 52, 80, 71, 67, 79, 58, 85, 66, 57, 84, 68, 64]
	}, 
  "Paso Peruano": {
    "index": 65,
    "colors": [ 10, 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5]
	}, 
  "Quarter Horse": {
    "index": 69,
    "colors": [ 10, 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5]
	}, 
  "Selle Francais": {
    "index": 90,
    "colors": [ 33, 26, 30, 27, 7, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Shagya-Araber": {
    "index": 74,
    "colors": [ 3, 33, 26, 35, 2, 32, 34]
	}, 
  "Tennessee Walker": {
    "index": 78,
    "colors": [ 5, 33, 26, 31, 30, 27, 28, 7, 2, 32, 16, 3, 12]
	}, 
  "Tinker": {
    "index": 70,
    "colors":[ 64, 56, 26, 54, 55, 53, 28, 7, 65, 2, 52, 34, 71, 16, 58, 3, 57]
	}, 
  "Trakehner": {
    "index": 44,
    "colors": [ 10, 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5]
	}, 
  "Belgisches Reitpony": {
    "index": 96,
    "colors":[33, 26, 31, 30, 27, 28, 7, 35, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Connemara-Pony": {
    "index": 82,
    "colors":[33, 26, 31, 30, 27, 28, 7, 35, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Deutsches Reitpony": {
    "index": 52,
    "colors": [33, 26, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5, 10]
	}, 
  "Haflinger": {
    "index": 41,
    "colors": [28,29,16]
	}, 
  "Highlandpony": {
    "index": 83,
    "colors": [33,26,27,28,7,2,32,34,3,12]
	}, 
  "Kerry Bog": {
    "index": 92,
    "colors": [ 33, 56, 26, 54, 30, 55, 7, 65, 2, 52, 32, 34, 71, 16, 58, 3, 57]
	}, 
  "Neufundland Pony": {
    "index": 51,
    "colors":  [ 33, 26, 31, 30, 27, 28, 7, 2, 29, 32, 34, 3, 12, 5, 10]
	}, 
  "Norweger": {
    "index": 50,
    "colors":  [59,60,61,62,63]
	}, 
  "Quarter Pony": {
    "index": 60,
    "colors": [33, 26, 77, 54, 31, 30, 55, 27, 53, 28, 7, 35, 2, 52, 29, 32, 34, 67, 16, 79, 58, 3, 66, 57, 12, 5, 10]
	}, 
  "Shetlandpony": {
    "index": 66,
    "colors":  [33, 26, 54, 31, 30, 55, 27, 53, 28, 7, 2, 52, 29, 32, 34, 71, 16, 58, 3, 57, 12, 5, 10]
	}, 
  "Welsh Cob": {
    "index": 55,
    "colors":  [10, 33, 26, 30, 27, 28, 7, 2, 29, 32, 34, 16, 3, 12, 5]
	}, 
  "Ban'ei Pferd": {
    "index": 98,
    "colors": [12, 33, 26, 2, 29, 32, 3]
	}, 
  "Drum Horse": {
    "index": 91,
    "colors":  [26,54,82,34,71,57,84]
	}, 
  "Percheron": {
    "index": 85,
    "colors":  [33,32,34,3]
	}, 
  "Shire": {
    "index": 86,
    "colors":  [30,32,3]
	}, 
  "Esel": {
    "index":57,
    "colors":  [4,3,1]
	}, 
};
  
</script>

<template>
  <div v-for="(colorIndex, color) in colors" :key="colorIndex">
    {{ color }} 
    
    <div v-for="(breed, type) in breeds"> 
      <div v-if="breed.colors.includes(colorIndex)">
        <a :href="'https://www.howrse.de/marche/vente/?chevalType=&amount=0&currency=soft&race-all='+breed.index+'&r'+breed.index+'='+colorIndex+'noFilter=1&advanced=1&tri=amount&sens=ASC&submit='" target="_blank"> 
        Equus
      </a> 
      / 
      <a :href="'https://www.howrse.de/marche/vente/?chevalType=&amount=0&currency=hard&race-all='+breedIndex+'&r'+breedIndex+'='+colorIndex+'noFilter=1&advanced=1&tri=amount&sens=ASC&submit='" target="_blank"> 
        Pässe
      </a>
       ( {{ type }} )
    	</div>
    </div>
    <br>
  </div>
</template>
