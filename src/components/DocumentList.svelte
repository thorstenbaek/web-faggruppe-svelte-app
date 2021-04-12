<h1>Document List</h1>

<script>
    import documents from "../data/documents.json";       
    import DocumentItem from "./DocumentItem.svelte";

    
</script>

<table>
    <thead>
        <th>Date</th>
        <th>Title</th>
        <th>Author</th>
    </thead>
    <tbody> 
        {#each documents as document}       
            <DocumentItem {document} />
        {/each}
    </tbody>
</table>

<style>
    table,th {
        border: 1px solid black;
        border-collapse: collapse;
    }

    th {
        padding: 2px 5px 2px 5px;
    }

    /* tr:nth-child(even) {background-color: #eeeeee;}
    tr:nth-child(odd) {background-color: #ffffff;} */

    table {                
        background: #eeeeee;
        width:50%;
        text-align: left;
    }
</style>