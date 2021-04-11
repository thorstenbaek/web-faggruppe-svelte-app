<h1>Document List</h1>

<script>
    import documents from "../data/documents.json";       

    const monthNames = ["January", "February", "March", "April", "May", "June",
        "July", "August", "September", "October", "November", "December"
    ];

    function formatDate(dateString) {
        var d = new Date(dateString);
        var now = new Date();
        if (now.getFullYear() == d.getFullYear()) {
            return `${String(d.getDate()).padStart(2, '0')}. ${monthNames[d.getMonth()]} ${String(d.getHours()).padStart(2, '0')}.${String(d.getMinutes()).padStart(2, '0')}`;
        }
        
        return `${String(d.getDate()).padStart(2, '0')}.${String(d.getMonth()).padStart(2, '0')}.${d.getFullYear()}`;
    }

    function formatName(s) {
        if (typeof s !== 'string') return ''
        var lowerCase = s.toLowerCase();
        return lowerCase.charAt(0).toUpperCase() + lowerCase.slice(1);        
    }

</script>

<table>
    <thead>
        <th>Date</th>
        <th>Title</th>
        <th>Last Name</th>
        <th>First Name</th>
    </thead>
    <tbody> 
        {#each documents as document}       
        <tr>            
            <td>{formatDate(document.eventTime)}</td>
            <td>{document.title}</td>
            <td>{formatName(document.author.lastName)}</td>        
            <td>{formatName(document.author.firstName)}</td>        
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