<script>
    import {localeStore} from "../stores/localeStore";

    var enIcon = '🇬🇧';
    var noIcon = '🇳🇴';
</script>
<ul>
    <li on:click={() => localeStore.set("en/us")} class={$localeStore == "en/us" ? "selected":""}>{enIcon}</li>
    <li on:click={() => localeStore.set("nb/no")} class={$localeStore == "nb/no" ? "selected":""}>{noIcon}</li>
</ul>

<style>
    ul {
        text-align: right;
    }
    li {
        display: inline-block;                
        padding: 2px;
    }
    li:hover {
        background: rgb(212, 233, 240);
        cursor: default;
    }

    .selected {
        background: skyblue;        
    }
</style>