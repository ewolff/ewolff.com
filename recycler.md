---
title: Recycler
---

Spam pollutes the internet. This recycler provides the ability to sort
spam messages into individual letters, allowing these valuable raw
materials to be reused, for example, in program code.

<textarea id="textInput" rows="5" placeholder="Enter the text"></textarea>

<button onclick="recycleText()">Recyceln</button>

## Sorted Text

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
     let sortedText = parts.sort((a, b) => a.localeCompare(b, "en")).join("");
     document.getElementById("output").textContent = sortedText;
   }
</script>

## Opening Message

Thank you for your message! It was unsolicited and provides no
value. Therefore, I have sorted its letters alphabetically so that you
can repurpose them in a new way. Of course, you can also use this
functionality yourself at
[https://ewolff.com/recycler](https://ewolff.com/recycler).
