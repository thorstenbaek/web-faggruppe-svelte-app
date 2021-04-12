<script>
    export let document;
    let displayDate;
    let author;

    const monthNames = ["January", "February", "March", "April", "May", "June",
        "July", "August", "September", "October", "November", "December"
    ];   

    $: {
        var d = new Date(document.eventTime);
        var now = new Date();
        if (now.getFullYear() == d.getFullYear()) {
            displayDate = `${String(d.getDate()).padStart(2, '0')}. ${monthNames[d.getMonth()]} ${String(d.getHours()).padStart(2, '0')}.${String(d.getMinutes()).padStart(2, '0')}`;
        }
        
        displayDate = `${String(d.getDate()).padStart(2, '0')}.${String(d.getMonth()).padStart(2, '0')}.${d.getFullYear()}`;
    }    

    function formatName(s) {
        if (typeof s !== 'string') return ''
        var lowerCase = s.toLowerCase();
        return lowerCase.charAt(0).toUpperCase() + lowerCase.slice(1);        
    }

    $: {
        author = `${formatName(document.author.lastName)}, ${formatName(document.author.firstName)}`;
    }
    
</script>

<tr>            
    <td>{displayDate}</td>
    <td>{document.title}</td>
    <td>{author}</td>        
</tr>        

<style>
    td {
        border: 1px solid black;
        border-collapse: collapse;
        padding: 2px 5px 2px 5px;
    }
</style>