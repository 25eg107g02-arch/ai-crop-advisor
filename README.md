# ai-crop-advisor
AI-Based Crop Selection and Suitability Advisor
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Crop Selection & Suitability Advisor</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background: #f3f8f4;
    color: #1f2937;
    line-height: 1.6;
}

header {
    background: linear-gradient(135deg, #176b43, #238b5a);
    color: white;
    padding: 28px 20px;
}

.header-content {
    max-width: 1100px;
    margin: auto;
    display: flex;
    align-items: center;
    gap: 15px;
}

.logo {
    font-size: 48px;
}

header h1 {
    font-size: 30px;
}

header p {
    opacity: 0.9;
    margin-top: 3px;
}

main {
    max-width: 1050px;
    margin: 30px auto;
    padding: 0 20px;
}

.hero {
    text-align: center;
    margin-bottom: 25px;
}

.hero h2 {
    color: #176b43;
    font-size: 29px;
    margin-bottom: 8px;
}

.hero p {
    color: #667085;
}

.card {
    background: white;
    padding: 30px;
    border-radius: 18px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.08);
}

.card h2 {
    color: #176b43;
    margin-bottom: 22px;
}

.form-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
}

.input-group {
    display: flex;
    flex-direction: column;
}

.input-group label {
    font-weight: bold;
    margin-bottom: 8px;
}

select, input {
    padding: 13px;
    border: 1px solid #cbd5e1;
    border-radius: 9px;
    font-size: 15px;
    background: white;
}

select:focus, input:focus {
    outline: 2px solid #5ab785;
}

button {
    width: 100%;
    margin-top: 25px;
    padding: 15px;
    border: none;
    border-radius: 9px;
    background: #176b43;
    color: white;
    font-size: 17px;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    background: #0f5132;
}

button:disabled {
    opacity: 0.7;
    cursor: not-allowed;
}

#resultSection {
    margin-top: 35px;
}

.result-title {
    margin-bottom: 20px;
}

.result-title h2 {
    color: #176b43;
}

.result-title p {
    color: #667085;
}

.crop-card {
    background: white;
    padding: 23px;
    margin-bottom: 18px;
    border-radius: 14px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.07);
    border-left: 6px solid #176b43;
}

.crop-card.top {
    border-left-color: #d49a00;
}

.crop-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 15px;
}

.crop-name {
    font-size: 22px;
    font-weight: bold;
}

.score {
    font-size: 26px;
    font-weight: bold;
    color: #176b43;
    white-space: nowrap;
}

.status {
    display: inline-block;
    margin-top: 7px;
    padding: 5px 12px;
    border-radius: 20px;
    background: #e6f5ed;
    color: #176b43;
    font-size: 13px;
    font-weight: bold;
}

.explanation {
    margin-top: 15px;
    color: #475467;
}

.info {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    margin-top: 18px;
}

.info-box {
    background: #f3f8f4;
    padding: 12px;
    border-radius: 8px;
}

.info-box strong {
    display: block;
    margin-bottom: 3px;
}

.warning {
    margin-top: 15px;
    padding: 12px;
    background: #fff4d6;
    color: #795600;
    border-radius: 8px;
}

.warning ul {
    margin-left: 20px;
}

.notice {
    margin-top: 25px;
    padding: 20px;
    background: #fff8e6;
    border: 1px solid #f0d27a;
    border-radius: 12px;
}

.notice h3 {
    margin-bottom: 8px;
}

.hidden {
    display: none;
}

footer {
    text-align: center;
    padding: 30px;
    margin-top: 40px;
    background: #163d2b;
    color: white;
}

footer p {
    margin-top: 5px;
    opacity: 0.8;
}

@media (max-width: 700px) {
    .form-grid {
        grid-template-columns: 1fr;
    }

    .crop-header {
        align-items: flex-start;
    }

    .info {
        grid-template-columns: 1fr;
    }

    header h1 {
        font-size: 24px;
    }

    .hero h2 {
        font-size: 23px;
    }
}
</style>
</head>

<body>

<header>
    <div class="header-content">
        <div class="logo">🌱</div>
        <div>
            <h1>AI Crop Advisor</h1>
            <p>Smart crop selection based on your farm conditions</p>
        </div>
    </div>
</header>

<main>

<section class="hero">
    <h2>🌾 Find the Right Crop for Your Farm</h2>
    <p>
        Enter your farm conditions and get ranked crop recommendations
        with clear explanations.
    </p>
</section>

<section class="card">
    <h2>👨‍🌾 Farm Profile</h2>

    <div class="form-grid">

        <div class="input-group">
            <label for="soil">🌱 Soil Type</label>
            <select id="soil">
                <option value="">Select soil</option>
                <option value="Black">Black Soil</option>
                <option value="Red">Red Soil</option>
                <option value="Clay">Clay Soil</option>
                <option value="Sandy">Sandy Soil</option>
                <option value="Loamy">Loamy Soil</option>
            </select>
        </div>

        <div class="input-group">
            <label for="season">🌦️ Season</label>
            <select id="season">
                <option value="">Select season</option>
                <option value="Kharif">Kharif</option>
                <option value="Rabi">Rabi</option>
                <option value="Summer">Summer</option>
            </select>
        </div>

        <div class="input-group">
            <label for="water">💧 Water Availability</label>
            <select id="water">
                <option value="">Select water availability</option>
                <option value="Low">Low</option>
                <option value="Medium">Medium</option>
                <option value="High">High</option>
            </select>
        </div>

        <div class="input-group">
            <label for="temperature">🌡️ Temperature (°C)</label>
            <input type="number" id="temperature" placeholder="Example: 28" min="0" max="60">
        </div>

    </div>

    <button id="recommendBtn" onclick="getRecommendations()">
        🔍 Get Crop Recommendations
    </button>
</section>

<section id="resultSection" class="hidden">

    <div class="result-title">
        <h2>🌾 Crop Recommendations</h2>
        <p id="conditionSummary"></p>
    </div>

    <div id="results"></div>

</section>

<section id="notice" class="notice hidden">
    <h3>⚠️ Important Decision-Support Notice</h3>
    <p>
        These recommendations are suggestions for decision support,
        not guaranteed crop outcomes.
    </p>
    <p>
        Actual results may depend on rainfall, pests, diseases,
        soil nutrients, seed quality, farming practices and market conditions.
    </p>
</section>

</main>

<footer>
    <h3>🌱 AI Crop Selection & Suitability Advisor</h3>
    <p>Mini Hackathon Prototype • Decision Support Only</p>
</footer>

<script>
const crops = {
    Rice: {
        soil: ["Clay", "Loamy"],
        season: ["Kharif", "Summer"],
        water: "High",
        minTemp: 20,
        maxTemp: 35,
        duration: "120–150 days"
    },
    Wheat: {
        soil: ["Loamy", "Clay"],
        season: ["Rabi"],
        water: "Medium",
        minTemp: 10,
        maxTemp: 25,
        duration: "120–150 days"
    },
    Maize: {
        soil: ["Loamy", "Sandy", "Clay"],
        season: ["Kharif", "Rabi", "Summer"],
        water: "Medium",
        minTemp: 18,
        maxTemp: 32,
        duration: "90–120 days"
    },
    Cotton: {
        soil: ["Black", "Loamy"],
        season: ["Kharif"],
        water: "Medium",
        minTemp: 21,
        maxTemp: 35,
        duration: "150–180 days"
    },
    Groundnut: {
        soil: ["Sandy", "Loamy"],
        season: ["Kharif", "Summer"],
        water: "Low",
        minTemp: 20,
        maxTemp: 30,
        duration: "100–120 days"
    },
    Tomato: {
        soil: ["Loamy", "Sandy"],
        season: ["Rabi", "Summer"],
        water: "Medium",
        minTemp: 18,
        maxTemp: 30,
        duration: "90–120 days"
    },
    Chilli: {
        soil: ["Loamy", "Sandy"],
        season: ["Kharif", "Rabi"],
        water: "Medium",
        minTemp: 18,
        maxTemp: 32,
        duration: "120–150 days"
    }
};

function getWaterScore(available, required) {
    const levels = { Low: 1, Medium: 2, High: 3 };
    const difference = levels[available] - levels[required];

    if (difference === 0) return 100;
    if (difference === 1) return 90;
    if (difference === -1) return 55;
    if (difference === 2) return 75;
    if (difference === -2) return 25;

    return 50;
}

function getTemperatureScore(temp, min, max) {
    if (temp >= min && temp <= max) return 100;
    if (temp >= min - 5 && temp < min) return 70;
    if (temp > max && temp <= max + 5) return 70;
    return 30;
}

function calculateScore(crop, soil, season, water, temperature) {
    const soilScore = crop.soil.includes(soil) ? 100 : 30;
    const seasonScore = crop.season.includes(season) ? 100 : 25;
    const waterScore = getWaterScore(water, crop.water);
    const temperatureScore =
        getTemperatureScore(temperature, crop.minTemp, crop.maxTemp);

    // Weighted suitability:
    // Soil 25%, Season 20%, Water 20%, Temperature 20%, Preference 15%
    // Preference is neutral (50) because no specific crop preference is entered.
    return Math.round(
        soilScore * 0.25 +
        seasonScore * 0.20 +
        waterScore * 0.20 +
        temperatureScore * 0.20 +
        50 * 0.15
    );
}

function createResult(name, crop, soil, season, water, temperature) {
    const score = calculateScore(
        crop, soil, season, water, temperature
    );

    const reasons = [];
    const warnings = [];

    if (crop.soil.includes(soil)) {
        reasons.push(`${soil} soil is suitable for ${name}.`);
    } else {
        warnings.push(`${name} is not a strong match for ${soil} soil.`);
    }

    if (crop.season.includes(season)) {
        reasons.push(`${season} season is suitable for this crop.`);
    } else {
        warnings.push(
            `${name} is mainly suitable during ${crop.season.join(", ")} season.`
        );
    }

    if (water === crop.water) {
        reasons.push(
            `Your ${water.toLowerCase()} water availability matches the crop requirement.`
        );
    } else if (
        water === "High" &&
        (crop.water === "Low" || crop.water === "Medium")
    ) {
        reasons.push("Available water is sufficient for this crop.");
    } else if (water === "Low" && crop.water !== "Low") {
        warnings.push(
            `This crop requires ${crop.water.toLowerCase()} water availability.`
        );
    } else if (water === "Medium" && crop.water === "High") {
        warnings.push("This crop normally needs high water availability.");
    }

    if (temperature >= crop.minTemp && temperature <= crop.maxTemp) {
        reasons.push(
            `${temperature}°C is within the preferred temperature range.`
        );
    } else {
        warnings.push(
            `Preferred temperature is ${crop.minTemp}–${crop.maxTemp}°C.`
        );
    }

    let status;

    if (score >= 80) {
        status = "HIGHLY SUITABLE";
    } else if (score >= 60) {
        status = "SUITABLE";
    } else if (score >= 40) {
        status = "MODERATELY SUITABLE";
    } else {
        status = "NOT RECOMMENDED";
    }

    return {
        name,
        score,
        status,
        reasons,
        warnings,
        water: crop.water,
        duration: crop.duration
    };
}

function getRecommendations() {
    const soil = document.getElementById("soil").value;
    const season = document.getElementById("season").value;
    const water = document.getElementById("water").value;
    const temperature =
        Number(document.getElementById("temperature").value);

    if (!soil || !season || !water || isNaN(temperature)) {
        alert("Please fill in all farm details.");
        return;
    }

    if (temperature < 0 || temperature > 60) {
        alert("Please enter a temperature between 0°C and 60°C.");
        return;
    }

    const button = document.getElementById("recommendBtn");
    button.disabled = true;
    button.textContent = "⏳ Analyzing...";

    // Small delay makes the prototype feel like it is processing data.
    setTimeout(() => {
        const results = [];

        for (const name in crops) {
            results.push(
                createResult(
                    name,
                    crops[name],
                    soil,
                    season,
                    water,
                    temperature
                )
            );
        }

        results.sort((a, b) => b.score - a.score);

        const container = document.getElementById("results");
        container.innerHTML = "";

        results.forEach((result, index) => {
            const card = document.createElement("div");
            card.className = "crop-card" + (index === 0 ? " top" : "");

            let warningsHTML = "";

            if (result.warnings.length > 0) {
                warningsHTML = `
                    <div class="warning">
                        <strong>⚠️ Considerations</strong>
                        <ul>
                            ${result.warnings.map(
                                warning => `<li>${warning}</li>`
                            ).join("")}
                        </ul>
                    </div>
                `;
            }

            card.innerHTML = `
                <div class="crop-header">
                    <div>
                        <div class="crop-name">
                            ${index + 1}. 🌱 ${result.name}
                        </div>
                        <span class="status">${result.status}</span>
                    </div>
                    <div class="score">${result.score}%</div>
                </div>

                <div class="explanation">
                    <strong>💡 Why this recommendation?</strong>
                    <p>${result.reasons.join(" ")}</p>
                </div>

                <div class="info">
                    <div class="info-box">
                        <strong>💧 Water Requirement</strong>
                        ${result.water}
                    </div>

                    <div class="info-box">
                        <strong>📅 Growing Duration</strong>
                        ${result.duration}
                    </div>
                </div>

                ${warningsHTML}
            `;

            container.appendChild(card);
        });

        document.getElementById("conditionSummary").textContent =
            `Soil: ${soil} • Season: ${season} • Water: ${water} • Temperature: ${temperature}°C`;

        document.getElementById("resultSection").classList.remove("hidden");
        document.getElementById("notice").classList.remove("hidden");

        document.getElementById("resultSection").scrollIntoView({
            behavior: "smooth"
        });

        button.disabled = false;
        button.textContent = "🔍 Get Crop Recommendations";
    }, 500);
}
</script>

</body>
</html>
