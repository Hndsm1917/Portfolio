}
document.addEventListener("DOMContentLoaded", ()=> { 
    const formla = document.querySelector('#formula')

    if(formla){
        formla.addEventListener('change' , ()=> {
            let activityMer = document.querySelectorAll('.activityMer')
            let activityDer = document.querySelectorAll('.activityDer')

            function activate(element){
                element.classList.add('display-flex')
                element.classList.remove('display-none')
            }
            function deactivate(element){
                element.classList.remove('display-flex')
                element.classList.add('display-none')
            }
            
            if(formla.value === 'MER'){
                activityMer.forEach(element => activate(element))
                activityDer.forEach(element => deactivate(element))
            }
            if(formla.value === 'DER'){
                activityMer.forEach(element => deactivate(element))
                activityDer.forEach(element => activate(element))
            }
        })
    }
})

function calculatorSubmit(){
    event.preventDefault()
    let form = document.querySelector('#calculator__form')
    let formula = form.formula.value
    let weight = form.weight.value
    let measure = form.measure.value
    let feed = form.feed.value

    let kcalDay = document.querySelector('#calc-pop-up__result1')
    let foodWeight = document.querySelector('#calc-pop-up__result2')
    let portionSize = document.querySelector('#calc-pop-up__result3')
    let calcPopUp = document.querySelector('.calculator__pop-up-background')
    let activ = document.querySelector('.activ')

    let min = activ.options[activ.selectedIndex].dataset.min
    let max = activ.options[activ.selectedIndex].dataset.max


    function checkMeasure(weightValue){
        if(measure === 'Kilogram'){
            return parseInt(weightValue)
        }
        else{
            console.log('when you use non-metric system of measurement, we cry')
            return  parseInt(weightValue * 0.45359237)
        }
    }
    let calcWeight = checkMeasure(weight)

    

    function calcWeightKormMin(kkalsMin, feed){       
        if(measure === 'Kilogram'){
            weightKormMin = (kkalsMin / feed)
            return weightKormMin
        }
        else{
            weightKormMin = (kkalsMin / feed) / 0.02834952
            return weightKormMin = (kkalsMin / feed) / 0.02834952
        }
    }
    function calcWeightKormMax(kkalsMax, feed){
        if(measure === 'Kilogram'){
            return weightKormMax = (kkalsMax / feed)
        }
        else{
            return weightKormMax = (kkalsMax / feed) / 0.02834952
        }
    }
    

    function calcMer(calcWeight, min, max, feed, measure){
        
        if(max != "0"){
            let kkalsMin = min * 132 * (Math.pow(calcWeight, 0.75))
            let kkalsMax = max * 132 * (Math.pow(calcWeight, 0.75))
            kcalDay.innerHTML = parseInt(kkalsMin) + ' - ' + parseInt(kkalsMax) + ' kcal/day'

            let weightKormMin = calcWeightKormMin(kkalsMin, feed)
            let weightKormMax = calcWeightKormMax(kkalsMax, feed)
            foodWeight.innerHTML = weightKormMin.toFixed(3) + ' - ' + weightKormMax.toFixed(3)  + " " + measure

            let portionSizeMin = weightKormMin / 2
            let portionSizeMax = weightKormMax / 2
            portionSize.innerHTML = portionSizeMin.toFixed(3) + ' - ' + portionSizeMax.toFixed(3)  + " " + measure
        }
        else{
            let kkalsMin = min * 132 * (Math.pow(calcWeight, 0.75))
            kcalDay.innerHTML = parseInt(kkalsMin) + ' kcal/day'

            let weightKormMin = calcWeightKormMin(kkalsMin, feed)
            foodWeight.innerHTML = weightKormMin.toFixed(3) + " " + measure
    
            let portionSizeMin = weightKormMin / 2
            portionSize.innerHTML = portionSizeMin.toFixed(3) + " " + measure
        }
        calcPopUp.classList.add('pop-up__on')
        body.classList.add('disable-overflow')
    }

    function calcDer(calcWeight, min, max, feed, measure){

        if(max != "0"){
            let kkalsMin = min * (Math.pow(calcWeight, 0.75))
            let kkalsMax = max * (Math.pow(calcWeight, 0.75))
            kcalDay.innerHTML = parseInt(kkalsMin) + ' - ' + parseInt(kkalsMax) + ' kcal/day'

            let weightKormMin = calcWeightKormMin(kkalsMin, feed)
            let weightKormMax = calcWeightKormMax(kkalsMax, feed)
            foodWeight.innerHTML = weightKormMin.toFixed(3) + ' - ' + weightKormMax.toFixed(3)  + " " + measure

            let portionSizeMin = weightKormMin / 2
            let portionSizeMax = weightKormMax / 2
            portionSize.innerHTML = portionSizeMin.toFixed(3) + ' - ' + portionSizeMax.toFixed(3)  + " " + measure
        }

        else{
            let kkalsMin = min * (Math.pow(calcWeight, 0.75))
            kcalDay.innerHTML = parseInt(kkalsMin) + ' kcal/day'
            
            let weightKormMin = calcWeightKormMin(kkalsMin, feed)
            foodWeight.innerHTML = weightKormMin.toFixed(3) + " " + measure
    
            let portionSizeMin = weightKormMin / 2
            portionSize.innerHTML = portionSizeMin.toFixed(3) + " " + measure
        }

        calcPopUp.classList.add('pop-up__on')
        body.classList.add('disable-overflow')
    }
    function calculator(){
        if(formula === 'MER'){
            calcMer(calcWeight, min, max, feed, measure)
        }
        else{
            calcDer(calcWeight, min, max, feed, measure)
        }
    }

    if(weight != 0 && feed != 0){
        calculator()
    }
    if(feed == 0){
        document.querySelector('.error__text').classList.add('display-block')
    }
    if(weight == 0){
        document.querySelector('.error__text').classList.add('display-block')
    }
}   
function closePopUp(){
    document.querySelector('.calculator__pop-up-background').classList.remove('pop-up__on')
    body.classList.remove('disable-overflow')
}
