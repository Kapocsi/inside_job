<script>
	import CssRest from '../reset.css.svelte';
</script>




<div class="container">
    <div class="shadow1"></div>
    <div class="shadow2"></div>
    <div class="modal">
        <div class="title">
            Gather Grid
        </div>
        <select>
            <option>1</option>
            <option>2</option>
        </select>
    </div>
</div>


<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        /* madefrom chat gpt */
        background: 
                linear-gradient(0deg, #f0f0f0 1px, transparent 1px),
                linear-gradient(90deg, #f0f0f0 1px, transparent 1px);
            background-size: 20px 20px;
    }

    .shadow2 {
        box-shadow: -150px -50px 200px 200px rgba(80, 180, 200, 0.5);
    }

    .shadow1 {
        box-shadow: 150px 50px 200px 200px rgba(30, 43, 200, 0.5)
    }

    .modal select {
        width: 100%;
        height: 25px;
        border-radius: 0.5rem;

    }

    .title {
        font-size: 3rem;
        font-weight: 900;
    }

</style>

