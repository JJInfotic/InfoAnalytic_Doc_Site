# Insert A New Document Page

1. Create a New Markdown File

   1. Create a new markdown file (`.md` extension) in the directory where your documentation resides. This is usually in the `docs/` directory at the root of your project. The name of the file will be used as the URL of the page (i.e., `my_new_page.md` will be accessible at `sitename.com/my_new_page`). 

2. Add Doc Content 
   
3. Update mkdocs.yml 

   1. After document md is updated, open `mkdocs.yml`, which is typically located at the root of your project.

   2. Under the `nav:` section update the site map. To add your new page, simply add a new line with the format `- Page Title: 'filename.md'`. Here, `Page Title` is what will appear in the navigation menu on your site, and `'filename.md'` is the path to your markdown file relative to `mkdocs.yml`.
   - Here's an example of what this might look like:

      ```bash
      nav:
          - Home: 'index.md'
          - User Guide: 'user-guide.md'
          - My New Page: 'my_new_page.md'  # your new page
      ```

4. **View the Doc Site (locally)**
   - After you've saved your changes to `mkdocs.yml`, build the site by running the command `mkdocs build` in your terminal. This will generate a new version of your site with all your changes.
   - To view your new page, start the MkDocs server with the command `mkdocs serve` and navigate to `localhost:8000` in your web browser. From there, you should be able to navigate to your new page via the navigation menu.
