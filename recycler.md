---
title: Recycler
---

Spam verschmutzt das Internet. Dieser Recycler bietet die Möglichkeit,
Spam-Nachrichten in einzelne Buchstaben zu sortieren, um diese
wichtigen Rohstoffe beispielsweise im Programm-Code wiederzuverwenden.

<textarea id="textInput" rows="5" placeholder="Gib deinen Text ein"></textarea>

<button onclick="recycleText()">Recyceln</button>

# Sortierter Text

<span id="output"></span>
    
<script>
   function recycleText() {
     let text = document.getElementById("textInput").value;
     let sortedText = text.split("").sort((a, b) => a.localeCompare(b, 'de')).join("");
     document.getElementById("output").textContent = sortedText;
   }
</script>

# Anschrieb

Danke für Ihre Nachricht! Sie ist unverlangt und bietet keinen
Wert. Ich habe daher ihre Nachricht nach Buchstaben sortiert, so dass
sie diese Buchstaben nun einer neuen Verwendung zuführen
können. Natürlich können Sie diese Funktionalität auch selber nutzen
unter [https://ewolff.com/recycler](https://ewolff.com/recycler).

# Opening Message

Thank you for your message! It was unsolicited and provides no
value. Therefore, I have sorted its letters alphabetically so that you
can repurpose them in a new way. Of course, you can also use this
functionality yourself at
[https://ewolff.com/recycler](https://ewolff.com/recycler).
