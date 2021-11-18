# Курсы

## Каталог рекомендованных курсов

Избранные учебные материалы для освоения исследовательских инструментов.


<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
* {
  box-sizing: border-box;
}

#myInput {
  background-image: url('/css/searchicon.png');
  background-position: 10px 10px;
  background-repeat: no-repeat;
  width: 100%;
  font-size: 16px;
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
  margin-bottom: 12px;
}

#myTable {
  border-collapse: collapse;
  width: 100%;
  border: 1px solid #ddd;
  font-size: 18px;
}

#myTable th, #myTable td {
  text-align: left;
  padding: 12px 20px 12px 40px;

}

#myTable tr {
  border-bottom: 1px solid #ddd;
}

#myTable tr.header, #myTable tr:hover {
  background-color: #f1f1f1;
}
</style>


<input type="text" id="myInput" onkeyup="myFunction()" placeholder="Enter code name..." title="Type in a name">

_Sort table columns alphabetically by clicking on headers_

</details>
<table id="myTable">
  <tr class="header">
    <th onclick="sortTable(0)" style="width:30%;">Code</th>
    <th onclick="sortTable(1)" style="width:80%;">Description</th>
    <th onclick="sortTable(2)" style="width:70%;">Category</th>
    <th onclick="sortTable(3)" style="width:80%;">Additional Material</th>
  </tr>
  <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/finix">FINIX</a></td>
    <td>A fuel performance code ...</td>
    <td>Open Source</td>
    <td>IFPE</td>
  </tr>
  <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/refit">REFIT</a></td>
    <td>A nuclear something code ...</td>
    <td>Open Source</td>
    <td>...</td>
  </tr>
  <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/penelope">PENELOPE</a></td>
    <td>A simulated electron-photon transport code ...</td>
    <td>Open Source</td>
    <td>SINBAD</td>
  </tr>
  <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/serpent-v1">Serpent</a></td>
    <td>A multipurpose Monte Carlo code ...</td>
    <td>Restricted</td>
    <td>ICSBEP, IPPhE</td>
  </tr>
  <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/MCNP">MCNP</a></td>
    <td>A multipurpose Monte Carlo code ...</td>
    <td>Restricted</td>
    <td>_--_</td>
  </tr>
  <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/FISPACT">FISPACT-II</a></td>
    <td>A multipurpose Monte Carlo code ...</td>
    <td>Restricted</td>
    <td>_--_</td>
  </tr>
    <tr>
    <td><a href="https://git2.oecd-nea.org/databank/cps/SCALE">SCALE</a></td>
    <td>A multipurpose Monte Carlo code ...</td>
    <td>Restricted</td>
    <td>_--_</td>
  </tr>
</table>






[Send feedback via mailto](mailto:programs@oecd-nea.org)

[NDS example](../nds/)
