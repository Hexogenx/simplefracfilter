// ==UserScript==
// @name           SimpleFrac
// @namespace      Hexogen
// @version        1
// @description    Remove search results without Tier 1 fractured mod
// @include        https://www.pathofexile.com/trade/search*
// ==/UserScript==

var getButton = document.createElement("input")
var removeButton = document.createElement("input")

function getArrays()
{
    var modlist = []
	var tier1items = []
	var allitems = Array.from(document.getElementsByClassName("row"))
	var fracmods = document.getElementsByClassName("fracturedMod")
    window.modlist = modlist
	window.tier1items = tier1items
	window.allitems = allitems
	window.fracmods = fracmods
}

function removeArrays()
{

    for (var i = 0; i < fracmods.length; i++)
    {
        modlist.push(fracmods[i].firstChild)
    }

    for (var i = 0; i < modlist.length; i++)
    {
        if (modlist[i].innerText == "P1" || modlist[i].innerText == "S1")
        {
            tier1items.push(modlist[i].parentElement.parentElement.parentElement.parentElement.parentElement.parentElement)
        }
    }

    for (var i = (allitems.length - 1); i >= 0; i--)
    {
        for(var j=0; j < tier1items.length; j++)
        {
            if(allitems[i] && (allitems[i].dataset.id === tier1items[j].dataset.id))
            {
                allitems.splice(i, 1)
            }
        }
    }

    for (var i = 0; i < allitems.length; i++)
	{
		allitems[i].remove()
	}
}

removeButton.type="button"
removeButton.value="REMOVE"
removeButton.onclick = removeArrays
document.body.append(removeButton)

getButton.type="button"
getButton.value="GET"
getButton.onclick = getArrays
document.body.append(getButton)
