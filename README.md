<script>
  
  
var stringMaxLine = 55;

function splitText(t, w){
 var lines = [];
 t = t.split(' ');
 var curline = '', testline;
 for(var i = 0; i < t.length; i++){
  testline = curline + t[i] + ' ';
  if(testline.length > w){
   lines.push(curline);
   curline = t[i] + ' ';
  } else {
   curline = testline;
  }
 }
 return lines.length === 0 ? [t.join(' ')] : lines.concat([curline]);
}

function normalizeNumber(n){
	n = parseInt(n);
	return n < 10 ? '0' + n : '' + n;
}

var sbvReg = /(\d+)\:(\d+)\:(\d+)\.(\d+)\,(\d+)\:(\d+)\:(\d+)\.(\d+)\n(.+)/;
var sbvRegGlobal = /(\d+)\:(\d+)\:(\d+)\.(\d+)\,(\d+)\:(\d+)\:(\d+)\.(\d+)\n(.+)/g;

function sbvToSrt(str, i){
 str = str.match(sbvReg);

 return (
`${i+1}
${normalizeNumber(str[1])}:${str[2]}:${str[3]},${str[4]} --> ${normalizeNumber(str[5])}:${str[6]}:${str[7]},${str[8]}
${splitText(str[9], stringMaxLine).join('\n')}`
 );
}

var srt = sub.match(sbvRegGlobal).map(sbvToSrt).join('\n\n');
</script>

## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/keyten/sbv-to-srt/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

<input type="text" />

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/keyten/sbv-to-srt/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
