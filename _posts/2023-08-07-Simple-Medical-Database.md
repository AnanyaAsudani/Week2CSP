---
toc: true
comments: true
layout: post
title: Basic Database
description: This is a simple database that has simple descriptions of diseases and links to help people learn more 
type: hacks
courses: { compsci: {week: 3} }
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Genetic Disease Database</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        #container {
            margin: 20px;
        }

        #disease-dropdown {
            width: 200px;
            padding: 10px;
            font-size: 16px;
        }

        #disease-description {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ccc;
        }

        #show-description-button {
            margin-top: 10px;
            padding: 5px 10px;
            font-size: 14px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>Genetic Disease Database</h1>
        <label for="disease-dropdown">Select a Genetic Disease:</label>
        <select id="disease-dropdown">
            <option value="" disabled selected>Select a disease</option>
            <option value="neurofibromatosis">Neurofibromatosis</option>
            <option value="parkinsons">Parkinson's Disease</option>
            <option value="alzheimers">Alzheimer's Disease</option>
            <option value="muscular-dystrophy">Muscular Dystrophy</option>
        </select>
        <button id="show-description-button">Show Description</button>
        <div id="disease-description">
            <!-- Disease descriptions will be displayed here -->
        </div>
    </div>

    <script>
        const diseaseDescriptions = {
            neurofibromatosis: "Neurofibromatosis is a genetic disorder that affects the nervous system and causes tumors to form on nerve tissue and can lead to other issues such as MPNST or cancers. Neurofibromatosis (NF) is a complex genetic disorder that arises from mutations in specific genes, primarily NF1 and NF2, and less commonly, SMARCB1 and LZTR1. NF1, known as von Recklinghausen's disease, typically presents with café-au-lait spots, neurofibromas (benign tumors along nerves and skin), and diverse clinical manifestations affecting various body systems, such as the nervous, musculoskeletal, and ocular systems. NF2 predominantly features bilateral vestibular schwannomas, which lead to sensorineural hearing loss and balance issues. Schwannomatosis, though the rarest form, is marked by severe pain arising from multiple schwannomas without the development of vestibular tumors. While NF tumors are generally non-malignant, they can cause substantial morbidity and impact an individual's quality of life. Ongoing research aims to unravel the underlying genetic mechanisms, improve diagnostics, and develop targeted therapies for this intriguing and often challenging condition. here are some links:                                                                                                           https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8349880/pdf/nihms-1706241.pd                                        https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3081157/                                                          https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7601777/",
            parkinsons: "Parkinson's disease is a neurodegenerative disorder that affects movement control and widely affects induviduals. Parkinson's disease is a progressive neurological disorder characterized by the degeneration of dopamine-producing neurons in the brain. It is primarily recognized by its motor symptoms, which include resting tremors, bradykinesia (slowness of movement), rigidity, and postural instability. These symptoms often lead to difficulties with everyday activities and can significantly impact an individual's quality of life. Beyond the motor symptoms, Parkinson's can also give rise to non-motor symptoms, such as cognitive changes, mood disturbances, sleep disruptions, and autonomic dysfunction. While the exact cause of Parkinson's disease remains elusive, both genetic factors and environmental influences are believed to contribute to its development. Current treatment approaches aim to alleviate symptoms and may include medications, physical therapy, and in some cases, surgical interventions like deep brain stimulation. Research continues in the pursuit of better understanding this complex condition and developing therapies that can slow or halt its progression. here are some links:                                                                                                         https://www.mayoclinic.org/diseases-conditions/parkinsons-disease/symptoms-causes/syc-20376055                 https://www.parkinson.org/understanding-parkinsons/what-is-parkinsons",
            alzheimers: "Alzheimer's disease is a progressive brain disorder that affects memory, thinking, and behavior. Alzheimer's disease is a devastating and progressive brain disorder that predominantly affects memory, thinking, and behavior. It is the most common cause of dementia among older adults. Alzheimer's is characterized by the accumulation of abnormal protein deposits in the brain, including beta-amyloid plaques and tau tangles, which disrupt the communication between brain cells and lead to their eventual death. As the disease advances, individuals with Alzheimer's experience a decline in cognitive function, including memory loss, impaired reasoning, and difficulty with language and problem-solving. Behavioral and personality changes often occur, causing distress to both the affected individual and their loved ones. The cause of Alzheimer's remains incompletely understood, though age and genetics play significant roles. Currently, there is no cure for Alzheimer's disease, and available treatments primarily focus on managing symptoms and providing support to enhance the quality of life for those affected. Some links are:                                                                                                             https://www.mayoclinic.org/diseases-conditions/alzheimers-disease/symptoms-causes/syc-20350447                  https://www.nia.nih.gov/health/alzheimers-disease-fact-sheet",
            'muscular-dystrophy': "Muscular dystrophy is a group of genetic diseases characterized by progressive muscle weakness. Muscular dystrophy encompasses a group of inherited genetic disorders that result in the progressive weakening and degeneration of muscle tissue. These conditions can manifest in various forms and severity levels, but they all share the common characteristic of muscle weakness that often begins in childhood. The most prevalent form, Duchenne muscular dystrophy, is caused by a mutation in the dystrophin gene and typically affects boys. Other forms include Becker muscular dystrophy, myotonic dystrophy, and facioscapulohumeral muscular dystrophy, among others. The loss of muscle function can significantly impact an individual's mobility and independence, often leading to the need for mobility aids and assistive devices. While there is no cure for muscular dystrophy, ongoing research focuses on developing therapies to alleviate symptoms, slow disease progression, and improve the quality of life for those living with these conditions. Multidisciplinary care teams that include physical therapy, occupational therapy, and medical management play a crucial role in addressing the complex challenges associated with muscular dystrophy. Here are some links:                                                                                   https://www.mayoclinic.org/diseases-conditions/muscular-dystrophy/symptoms-causes/syc-20375388                 https://www.mayoclinic.org/diseases-conditions/muscular-dystrophy/symptoms-causes/syc-20375388",
        };

        const diseaseDropdown = document.getElementById('disease-dropdown');
        const diseaseDescription = document.getElementById('disease-description');
        const showDescriptionButton = document.getElementById('show-description-button');

        showDescriptionButton.addEventListener('click', function () {
            const selectedDisease = diseaseDropdown.value;
            if (selectedDisease in diseaseDescriptions) {
                diseaseDescription.innerText = diseaseDescriptions[selectedDisease];
            } else {
                diseaseDescription.innerText = 'Select a disease to view its description.';
            }
        });
    </script>
</body>
</html>
