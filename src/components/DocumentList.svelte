<script>

    import documents from "../data/documents.json";       
    import DocumentItem from "./DocumentItem.svelte";

    let myDocuments = documents;

    const byEventTime = (a, b) => 
			(a.eventTime < b.eventTime) ? -1 : (a.eventTime > b.eventTime) ? 1 : 0;
    const byTitle = (a, b) => 
			(a.title < b.title) ? -1 : (a.title > b.title) ? 1 : 0;
    const byAuthor = (a, b) => 
			(a.author.lastName < b.author.lastName) ? -1 : (a.author.lastName > b.author.lastName) ? 1 : 0;
    const byType = (a, b) => 
			(a.type < b.type) ? -1 : (a.type > b.type) ? 1 : 0;

    function sort(method) {

        myDocuments = myDocuments.sort(method);
        
    }    
</script>

<h2>Documents</h2>
<table>
    <thead>
        <th class="symbol" on:click={() => sort(byType)}/>
        <th on:click={() => sort(byEventTime)}>Date</th>
        <th on:click={() => sort(byTitle)}>Title</th>
        <th on:click={() => sort(byAuthor)}>Author</th>
    </thead>
    <tbody> 
        {#each myDocuments as document}       
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
        background: #eeeeee;
        padding: 2px 5px 2px 5px;
    }

    table {                        
        width:100%;
        text-align: left;
    }

    .symbol {
        width: 20px;
    }
</style>