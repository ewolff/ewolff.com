---
title: Recycler
layout: de
---

Spam verschmutzt das Internet. Dieser Recycler bietet die Möglichkeit,
Spam-Nachrichten in einzelne Buchstaben zu sortieren, um diese
wichtigen Rohstoffe beispielsweise im Programm-Code wiederzuverwenden.

<textarea id="textInput" rows="5" placeholder="Gib deinen Text ein"></textarea>

<button onclick="recycleText()">Recyceln</button>

## Sortierter Text

<span id="output"></span>

<script>
   function recycleText() {
     let text = document.getElementById("textInput").value;
     let Segmenter = window.Intl && Intl.Segmenter;
     let parts = [];
     if (Segmenter) {
       for (let { segment } of new Segmenter().segment(text)) {
         parts.push(segment);
       }
     } else {
       parts = text.split("");
     }
     let sortedText = parts.sort((a, b) => a.localeCompare(b, "de")).join("");
     document.getElementById("output").textContent = sortedText;
   }
</script>

## Anschrieb

Danke für Ihre Nachricht! Sie ist unverlangt und bietet keinen
Wert. Ich habe daher ihre Nachricht nach Buchstaben sortiert, so dass
sie diese Buchstaben nun einer neuen Verwendung zuführen
können. Natürlich können Sie diese Funktionalität auch selber nutzen
unter [https://ewolff.com/recycler-de](https://ewolff.com/recycler-de).

