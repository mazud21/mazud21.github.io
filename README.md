## Welcome to GitHub Pages
atest
You can use the [editor on GitHub](https://github.com/mazud21/mazud21.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

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

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/mazud21/mazud21.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

<!DOCTYPE html>
<html>
  <head>
    <title>API Data Table</title>
  </head>
  <body>
    <h1>API Data Table</h1>
    <table id="data-table" border="1">
      <thead>
        <tr>
          <th>Product ID</th>
          <th>Shop ID</th>
          <th>Status</th>
          <th>Name</th>
        </tr>
      </thead>
      <tbody id="table-body">
        <!-- Table rows will be added here -->
      </tbody>
    </table>

    <script>
      const myHeaders = new Headers();
      myHeaders.append("Authorization", "Bearer c:T3Eq-HdAS4Kjmy7gBhtUIA");
      myHeaders.append("Content-Type", "application/x-www-form-urlencoded");
      myHeaders.append("Access-Control-Allow-Credentials", "*");

      const requestOptions = {
        mode: "cors",
        method: "GET",
        headers: myHeaders,
        redirect: "follow",
      };

      const apiUrl =
        "https://fs.tokopedia.net/inventory/v1/fs/18412/product/info?shop_id=2242080&page=1&per_page=2";

      const tableBody = document.getElementById("table-body");

      fetch(apiUrl, requestOptions)
        .then((response) => response.json()) // Parse response as JSON
        .then((data) => {
          data.data.forEach((product) => {
            const row = document.createElement("tr");
            row.innerHTML = `
                        <td>${product.basic.productID}</td>
                        <td>${product.basic.shopID}</td>
                        <td>${product.basic.status}</td>
                        <td>${product.basic.name}</td>
                    `;
            tableBody.appendChild(row);
          });
        })
        .catch((error) => console.error("Error:", error));
    </script>
  </body>
</html>

