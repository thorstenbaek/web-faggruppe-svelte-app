<script>
    import {localeStore} from "../stores/localeStore.js";


    export let document;
    let displayDate;
    let author;

    const enMonthNames = ["January", "February", "March", "April", "May", "June",
            "July", "August", "September", "October", "November", "December"];   

    const noMonthNames = ["januar", "februar", "mars", "april", "mai", "juni",
        "juli", "august", "september", "oktober", "november", "desember"];       

    const typeImages = {
        "text":"📄",
        "image":"🖼"
    }

    $: {
        const d = new Date(document.eventTime);
        const now = new Date();

        if ($localeStore === "en/us") {                                
            if (now.getFullYear() == d.getFullYear()) {
                displayDate = `${enMonthNames[d.getMonth()]} ${d.getDate()}. ${String(d.getHours()).padStart(2, '0')}.${String(d.getMinutes()).padStart(2, '0')}`;
            } else {
                displayDate = `${d.getFullYear()}-${String(d.getMonth()).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')}`;
            }
        } else if ($localeStore === "nb/no") {
            if (now.getFullYear() == d.getFullYear()) {
                displayDate = `${d.getDate()}. ${noMonthNames[d.getMonth()]} ${String(d.getHours()).padStart(2, '0')}.${String(d.getMinutes()).padStart(2, '0')}`;
            } else {            
                displayDate = `${String(d.getDate()).padStart(2, '0')}.${String(d.getMonth()).padStart(2, '0')}.${d.getFullYear()}`;
            }
        }

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
    <td>{typeImages[document.type]}</td>   
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