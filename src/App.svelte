<script>
    // CSS
    import normalize from './css/normalize.css';
    import postmedia from './css/postmedia.css';
    import colours from './css/colors.css';
    import fonts from './css/fonts.css';
    import css from './css/main.css';

    // VARS
    let currentStep, iframe;
    
    // COMPONENTS
    import Steps from '$components/Steps.svelte';

    // SET CHART HEIGH & URL HERE...
    const chartHeight = '450px';
    const flourishStoryUrl = 'https://flo.uri.sh/story/3182108/embed';

    // FUNCTIONS
    const updateStep = function(currentStep) {
        iframe = document.querySelector('#app .chart > iframe');
        iframe.src = iframe.src.replace(/#slide-.*/, '') + '#slide-' + currentStep;
    }
    
    // conditional block to trigger step change on scroll
    $: {
        if (currentStep === 0) {
           updateStep(currentStep);
        } else if (currentStep === 1) {
            updateStep(currentStep);
        } else if (currentStep === 2) {
            updateStep(currentStep );
        } else if (currentStep === 3) {
            updateStep(currentStep);
        } else if (currentStep === 4) {
            updateStep(currentStep);
        }
    };
</script>

<!-- MARKUP -->
<section class="scrollyteller sticky">
    <header>
        <h1>Mayor’s office costs up under Sim</h1>
        <p class="subhead">Annual expenses from the Vancouver mayor's office for the city of Vancouver.</p>
    </header>
    <div class="chart sticky">
        <!-- svelte-ignore a11y-missing-attribute -->
        <iframe src={flourishStoryUrl} frameborder='0' scrolling='no' style="width:100%;height:{chartHeight};" title="flourish-embed"></iframe>
        <!-- NOTE: add `class="no-pointer"` to iframe if touch scrolling doesn't work -->
    </div>

<footer>
    <p class="source">Source:
        <a href="https://opendata.vancouver.ca/explore/dataset/council-budget-and-expenses/table/?sort=year" target="_blank">City of Vancouver</a>
    </p>
    <!-- flourish logo -->
    <div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/visualisation/3706064/?utm_source=embed&utm_campaign=visualisation/3706064' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
</footer>

</section>


<ul class="steps">
    <Steps bind:currentStep={currentStep}/>
</ul>

<!-- CSS -->
<style>
    /* STEPS */
    section {
        position: relative;
    }
    .sticky { 
        align-items: center;
        justify-content: center;
        margin-bottom: 1.5rem;
        position: sticky;
        top: 5vh;
        z-index: 1;
    }
    .chart .no-pointer {
        pointer-events: none;
    }
    .steps {
    margin-top: -110%;
        position: relative;
        z-index: 2;
    }
    @media only screen and (max-width: 450px) {
    /* Style adjustments for viewports that meet the condition */
         .steps {
            margin-top: -150%; 
        }
    }
</style>