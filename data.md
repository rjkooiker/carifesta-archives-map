---
layout: page
title: Data
---

<p>Here you can explore the data yourself.</p>


<h2>Tabular Data</h2>
<div style="overflow-x:auto;">
  <table id="dataTable" class="display nowrap" style="width:100%">
      <thead>
          <tr>
              <th>PID</th>
              <th>Repo URL</th>
              <th>Label</th>
              <th>Creator</th>
              <th>Code</th>
              <th>Type</th>
              <th>Repository</th>
              <th>Coordinates</th>
              <th>Repo Type</th>
              <th>Folders</th>
              <th>Description</th>
              <th>Festival Edition</th>
              <th>Languages</th>
              <th>Accession Date</th>
              <th>Digital</th>
              <th>Finding Aid</th>
              <th>Access Status</th>
              <th>Date Added</th>
          </tr>
      </thead>
      <tbody>
          <!-- Data will be populated here by DataTables.js -->
      </tbody>
  </table>
</div>

<p><a href="{{ site.baseurl }}/assets/carifesta.csv" download>Download CSV</a></p>

<script>
$(document).ready(function() {
    Papa.parse("{{ site.baseurl }}/assets/carifesta.csv", {
        download: true,
        header: true,
        complete: function(results) {
            $('#dataTable').DataTable({
                data: results.data,
                scrollX: true,
                columns: [
                    { "data": "pid" },
                    { 
                      "data": "repo_url",
                      "render": function(data, type, row) {
                          return '<a href="' + data + '" target="_blank">' + data + '</a>';
                      }
                    },
                    { "data": "label" },
                    { "data": "creator" },
                    { "data": "code" },
                    { "data": "type" },
                    { "data": "repository" },
                    { "data": "coordinates" },
                    { "data": "repo_type" },
                    { "data": "folders" },
                    { "data": "description" },
                    { "data": "festival_edition" },
                    { "data": "languages" },
                    { "data": "accession_date" },
                    { "data": "digital" },
                    { "data": "finding_aid" },
                    { "data": "access_status" },
                    { "data": "date_added" }
                ]
            });
        }
    });
});
</script>