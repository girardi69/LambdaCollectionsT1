## Welcome to my lambda collections T3

You can use the [editor on GitHub](https://github.com/girardi69/LambdaCollections/edit/gh-pages/index.md) to maintain and preview the content for you T4  

```markdown
Syntax highlighted code block

# Header 1

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](https://github.com/girardi69/LambdaCollectionsT1/blob/gh-pages/img/7768E4E5-A467-4B98-91ED-CA4695D740F7.jpeg)
```
![GitHub Logo](https://github.com/girardi69/LambdaCollectionsT1/blob/gh-pages/img/7768E4E5-A467-4B98-91ED-CA4695D740F7.jpeg)

```javascript
let i = 1;

exports.fi = function(event, context, callback) {

    console.log(i++);
    var html = '<html><head><title>HTML from API Gateway/Lambda</title></head>' + 
        '<body><h1>This is the Udemy Example API with external initialization: '  + JSON.stringify(i-1) + '</h1></body></html>';  
    context.succeed(html);
    
};

```
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/girardi69/LambdaCollections/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
