---
layout: post
title: Decibel-Watts per square meter Converter
---

This is a quick JavaScript project I whipped up because my calculator doesn't have functions. It converts between decibels and watts per square meter. There's not really any of error recovery or anything of that sort. Really simple, but it gets the job done.

<table>
    <tr>
        <td>To Decibels</td>
        <td>Output</td>
    </tr>
    <tr>
        <td>
            <input id="decibelsInput" onchange="decibelsInputEvent()"></input>
        </td>
        <td>
            <input id="decibelsOutput" disabled="true"></input>
        </td>
    </tr>
</table>

<table>
    <tr>
        <td>To Watts-per-square-meter</td>
        <td>Output</td>
    </tr>
    <tr>
        <td>
            <input onchange="wmInputEvent()" id="wmInput"></input>
        </td>
        <td>
            <input disabled="true" id="wmOutput"></input>
        </td>
    </tr>
</table>

Get the [Gist](https://gist.github.com/jadar/10221308) over on Github. Mess with the code on [JSBin](http://jsbin.com/xufohiqu/1/edit?html,js,output).

<script>
    Math.logBase = function (x, base) {
        var baseLog = 0;

        // don't use resources if they're already constants.
        if (base == 10) {
            baseLog = Math.LN10;
        } else if (base == 2) {
            baseLog = Math.LN2;
        } else {
            baseLong = Math.log(base);
        }

        return Math.log(x) / baseLog;
    };

    Math.log10 = function (x) {
        return Math.logBase(x, 10);
    };

    function toDb(wm) {
        return 10 * (Math.log10(wm / Math.pow(10, -12)));
    }

    function toWm(db) {
        return Math.pow(10, db / 10) * Math.pow(10, -12);
    }

    var decibelsInput = document.getElementById("decibelsInput");
    var decibelsOutput = document.getElementById("decibelsOutput");

    var wmInput = document.getElementById("wmInput");
    var wmOutput = document.getElementById("wmOutput");

    function decibelsInputEvent() {
        var db = toDb(decibelsInput.value);
        if (isNaN(db)) {
            decibelsOutput.value = "Error";
        } else {
            decibelsOutput.value = db;
        }
    }

    function wmInputEvent() {
        var wm = toWm(wmInput.value);
        if (isNaN(wm)) {
            wmOutput.value = "Error";
        } else {
            wmOutput.value = wm;
        }
    }
    
    console.log(decibelsInput);
</script>