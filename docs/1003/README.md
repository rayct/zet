

To add a build date to the bottom of the page in MkDocs, you can use the MkDocs built-in feature called "Variables." Variables allow you to define custom variables in your MkDocs configuration file (usually named `mkdocs.yml`), and then reference those variables in your Markdown pages. Here's how you can add a build date using variables:

Step 1: Configure `mkdocs.yml`:

Open your `mkdocs.yml` configuration file and add a new variable under the `extra` section. If the `extra` section doesn't exist, you can create it:

```yaml
site_name: Your Site Name
# Other configuration options...

extra:
  build_date: '%Y-%m-%d %H:%M:%S'
```

In this example, we've defined a variable named `build_date` with a date format `'%Y-%m-%d %H:%M:%S'`. The format uses Python's `strftime` syntax.

Step 2: Reference the variable in your Markdown pages:

Now, in your Markdown files (e.g., `index.md`, `about.md`, etc.), you can use the variable by referencing it as `{% variable_name %}`. In our case, it's `{% build_date %}`. Place this reference at the bottom of your desired Markdown page.

For example:

```markdown

# Welcome to My MkDocs Site

This is some content for your page.

Last built: {% build_date %}
```

Step 3: Build your MkDocs site:

After you've added the variable references to your Markdown files, build your MkDocs site again. Use the following command in your terminal or command prompt:

```bash
mkdocs build
```

The build process will render your Markdown pages with the build date variable, and you'll find the date displayed at the bottom of each page when you view your site.

Remember that the build date will only update when you rebuild the MkDocs site. So, if you want to update the build date, you'll need to run `mkdocs build` again before deploying the site.
