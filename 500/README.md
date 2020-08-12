... breadcrumbs ...

# 500 Create a Basic CRUD Application

Video at 20:36 https://www.youtube.com/watch?v=Z1RJmh_OqeA&list=PLYqVE-1VuKv63jvgb3kvY1P63EAkfACTP&index=127

Update 'templates/index.html' file as follows:

```
...
{% block body %}
<div class="content">
  <h1>Task Master</h1>
  <table>
    <tr>
      <th>Task</th>
      <th>Added</th>
      <th>Actions</th>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>
        <a href="">Delete</a>
        <br>
        <a href="">Update</a>
      </td>
    </tr>
  </table>
</div>
{% endblock %}
...

```

