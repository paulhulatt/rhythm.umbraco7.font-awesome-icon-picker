$.get('https://raw.githubusercontent.com/FortAwesome/Font-Awesome/master/advanced-options/metadata/icons.yml', function(data){    
    var parsedYaml = jsyaml.load(data);
    var body = $('body');
    var brands = '&lt;option value=""&gt;--- BRANDS ---&lt;/option&gt;<br/>';
    var regular = '&lt;option value=""&gt;--- REGULAR ---&lt;/option&gt;<br/>';
    var solid = '&lt;option value=""&gt;--- SOLID ---&lt;/option&gt;<br/>';
    //body.append('<pre>');
    $.each(parsedYaml, function(index, icon){
    	$.each(icon.styles, function(styleindex, style){
      	//body.append(style);
      	switch(style) {
        	case 'brands':
          	brands += '&lt;option value="fab fa-' + index + '"&gt;' + icon.label + '&lt;/option&gt;<br/>';
            break;
          case 'regular':
          	regular += '&lt;option value="far fa-' + index + '"&gt;' + icon.label + '&lt;/option&gt;<br/>';
            break;
          case 'solid':
          	solid += '&lt;option value="fas fa-' + index + '"&gt;' + icon.label + '&lt;/option&gt;<br/>';
            break;
          default:
          	break;
        }
    		
        })
    })
    body.append(regular);
    body.append(solid)
    body.append(brands);
});