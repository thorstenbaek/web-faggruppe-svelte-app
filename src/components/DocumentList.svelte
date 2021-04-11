<h1>Document List</h1>

<script>
    import documents from "../data/documents.json";       
</script>

<table>
    <thead>
        <th>Date</th><th>Title</th><th>Last Name</th><th>First Name</th>
    </thead>
    <tbody> 
        {#each documents as document}       
        <tr>            
            <td>{document.eventTime}</td>
            <td>{document.title}</td>
            <td>{document.author.lastName}</td>        
            <td>{document.author.firstName}</td>        
        </tr>        
        {/each}
    </tbody>
</table>

<style>
    table,th,td {
        border: 1px solid black;
        border-collapse: collapse;
    }

    th, td {
        padding: 2px 5px 2px 5px;
    }

    tr:nth-child(even) {background-color: #eeeeee;}
    tr:nth-child(odd) {background-color: #ffffff;}

    table {                
        background: #eeeeee;
        width:50%;
        text-align: left;
    }
</style>