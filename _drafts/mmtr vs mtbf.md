formula for calculating availability:
availability = mtbf/(mtbf + mttr)

let's say we started with mtbf 60 and mttr 20, which gives 75% availability
if we optimize for mtbf and increase mtbf by 1 with every step -> 75.3, 75.6, 75.9
if we optimize for mtbf and decrease mttr by 1 with every step -> 75.9, 76.92, 77.92

conclusion:
decreasing mttr increases availability way faster.