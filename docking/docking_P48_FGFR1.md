
## Решения молекулярного докинга пептида P48 с рецептором FGFR1 (PDB ID 5W59, домены d2-d3)
[Назад](http://intbio.github.io/RNF_24-14-00250/year1.html)

<html lang="en">
<head>
  <meta charset="utf-8">
</head>
<body>
<br>
  <p style="color:#d6d6d6;font-size:22px;font-family:verdana;font-weight: bold;text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;display: inline">FGFR1, домены d2-d3 (PDB ID 5W59)</p>
<!--   <p style="color:#fc03ec;font-size:22px;font-family:verdana;font-weight: bold;text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black">Пептид EARGIHCHSIR</p> -->
 
<table border="solid 1px;" style="font-size:14px;">
<tr>
<th> Показать </th> <th>Решение докинга </th> <th> GalazyDock score </th><th>Энергия, ккал/моль (FoldX) </th><th>Скачать PDB </th>
</tr>

<tbody>
  
  <script src="https://unpkg.com/ngl@2.0.0-dev.35/dist/ngl.js"></script>
  <script src="https://code.jquery.com/jquery-3.5.1.min.js" integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0=" crossorigin="anonymous"></script>
  <script>
  

   var names = ['docking_str/P48_FGFR1_1.pdb', 'docking_str/P48_FGFR1_2.pdb', 'docking_str/P48_FGFR1_3.pdb', 'docking_str/P48_FGFR1_4.pdb', 'docking_str/P48_FGFR1_5.pdb', 'docking_str/P48_FGFR1_6.pdb', 'docking_str/P48_FGFR1_7.pdb', 'docking_str/P48_FGFR1_8.pdb', 'docking_str/P48_FGFR1_9.pdb', 'docking_str/P48_FGFR1_10.pdb']
   var models =  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] 
   var galaxy_scores = [0.389,0.383,0.338,0.327,0.329,0.333,0.293,0.324,0.333,0.324]
   var energies = [-2.683,-3.528,-5.325,-4.392,-4.852,-7.017,-6.032,-4.73,-1.181,-0.124]
   peptide_reps = [];
    $(document).ready(function() {
      window.stage = new NGL.Stage("viewport",{ backgroundColor:"#FFFFFF" });
      window.stage.loadFile("docking_str/P48_FGFR1_1.pdb").then(function (ref_pdb) {
        var aspectRatio = 2;
        var radius = 1.5;

        ref_pdb.addRepresentation('cartoon', {
           "sele": ":A ", "color": 0xd6d6d6,"aspectRatio":aspectRatio, "radius":radius,"radiusSegments":1,"capped":0 });;
        ref_pdb.autoView();
      });

      var arrayLength = names.length;
      var k;

    var hyper_scheme = NGL.ColormakerRegistry.addSelectionScheme([
        ["orange", ".CA"],
        ['0xecf0f1', '_H'],
        ["blue", "_N"],
        ["red", "_O"],
        ["cyan", "*"]
      ], "DA");
		for (k = 0; k < arrayLength; k++) {
            window.stage.loadFile(`${names[k]}`).then(function (ref_pdb) {
                var repr = ref_pdb.addRepresentation('hyperball', {
                   "sele": ":B", "color": hyper_scheme});
                repr.setVisibility(false);
                peptide_reps.push(repr);
               
          	});
		}
    
    window.stage.viewerControls.spin( [ 0, 1, 0 ],110 )
    });
    var arrayLength = names.length;
			for (var i = 0; i < arrayLength; i++) {
        
        document.write(`<tr><td> <input type="checkbox" id="${i}" name="${names[i]}"></td> <td>  ${models[i]}  </td> <td> ${galaxy_scores[i]} </td><td> ${energies[i]} </td></td><td> <a href="https://intbio.org/RNF_24-14-00250/docking/${names[i]}" download>PDB</a> </td></tr>`); 
			}
		  
      
$('input[type=checkbox]').on('change', toggle_reference_structure);

function toggle_reference_structure() {
               var state = $(this).is(":checked");
               var name = $(this).attr('id');
               peptide_reps[name].setVisibility(state)
          }


  </script>
  <div id="viewport" style="width:500px; height:500px; border: thin solid black"></div>
  </tbody>	
</table>
</body>
</html>
