---
title: Grade Calculator
layout: default
description: Supports grade inputs and calculates average. 
permalink: /frontend/grade_calc
categories: [pbl]
tags: [javascript, input, onblur]
---

<div class="container bg-primary">
    <header class="pb-3 mb-4 border-bottom border-primary text-dark">
        <span class="fs-4">Grade Calculator</span>
    </header>
    Total   : <input type="number" name="total" id="total" readonly/>
    Count   : <input type="number" name="count" id="count" readonly/>
    Average : <input type="number" name="average" id="average" readonly/>
    <br><br>
    Input scores, press tab to add new number:
    <div id="scores">
        <input onblur="calculator()" type="text" name="score" id="score0"/><br>
        <!-- javascript generated inputs -->
    </div>
</div>

<script>
    const scoreContainer = document.getElementById("scores");

    function newInputLine(index) {
        // make another input line
        var input = document.createElement("input");
        input.setAttribute('onblur', "calculator()");
        input.setAttribute('type', "text");
        input.setAttribute('name', "score");
        input.setAttribute('id', "score" + index);
        scoreContainer.appendChild(input);
        var br = document.createElement("br");
        scoreContainer.appendChild(br);
        document.getElementById("score" + index).focus();
    }

    function calculator(){
        var total = 0;  // running total
        var array = document.getElementsByName('score');
        for(var i = 0; i < array.length; i++){  // iterate through all matching input element
            if(parseInt(array[i].value))  // convert to int and 
                total += parseInt(array[i].value);  // running total update
        }
        document.getElementById('total').value = total;
        document.getElementById('count').value = array.length;
        document.getElementById('average').value = total / array.length;
        newInputLine(array.length);
    }

</script>