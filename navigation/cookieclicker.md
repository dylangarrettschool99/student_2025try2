---
layout: page
title: Cookie Clicker
permalink: /cookieclicker/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
            text-align: center;
        }

        .cookie-clicker-container {
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            max-width: 600px;
            margin: 20px auto;
        }

        #cookieButton, .upgrade-button {
            font-size: 1rem;
            padding: 10px 20px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            margin: 5px;
            background-color: #f8c291;
            color: #fff;
        }

        #cookieButton:hover, .upgrade-button:hover {
            background-color: #e67e22;
        }

        .flex-container, .upgrade-container {
            display: flex;
            justify-content: center;
            margin: 10px 0;
        }

        .flex-item, .upgrade-item {
            margin: 0 15px;
            font-size: 1.5rem;
        }
    </style>
</head>
<body>
    <div class="cookie-clicker-container">
        <h1>Cookie Clicker</h1>

        <div class="flex-container">
            <div class="flex-item">Cookies: <span id="cookieCount">0</span></div>
            <div class="flex-item">All-Time Cookies: <span id="allTimeCookies">0</span></div>
        </div>

        <button id="cookieButton">🍪 Click me!</button>

        <div class="upgrade-container">
            <div class="upgrade-item">Cookies per click: <span id="cookiesPerClick">1</span></div>
            <div class="upgrade-item">Cookies per second: <span id="cps">0</span></div>
        </div>

        <button id="clickUpgradeButton" class="upgrade-button">
            Upgrade Cookies Per Click (Cost: <span id="clickUpgradeCost">5</span> cookies)
            <span id="clickUpgradeCount">0</span> upgrades purchased
        </button>
        <button id="cpsUpgradeButton" class="upgrade-button">
            Upgrade Cookies Per Second (Cost: <span id="cpsUpgradeCost">5</span> cookies)
            <span id="cpsUpgradeCount">0</span> upgrades purchased
        </button>
        <button id="multiplierUpgradeButton" class="upgrade-button">
            Upgrade Multiplier (Cost: <span id="multiplierUpgradeCost">350</span> cookies)
            <span id="multiplierUpgradeCount">0</span> upgrades purchased
        </button>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            let cookieCount = 0;
            let allTimeCookies = 0;
            let cookiesPerClick = 1;
            let cookiesPerSecond = 0;
            let clickUpgradeCost = 5;
            let cpsUpgradeCost = 5;
            let multiplierUpgradeCost = 350;
            let clickIncrement = 1;
            let cpsIncrement = 1;
            let multiplier = 1;
            let multiplierMultiplier = 2;

            // Upgrades purchased counters
            let clickUpgradesPurchased = 0;
            let cpsUpgradesPurchased = 0;
            let multiplierUpgradesPurchased = 0;

            const elements = {
                cookieButton: document.getElementById('cookieButton'),
                cookieCountDisplay: document.getElementById('cookieCount'),
                allTimeCookiesDisplay: document.getElementById('allTimeCookies'),
                cookiesPerClickDisplay: document.getElementById('cookiesPerClick'),
                cpsDisplay: document.getElementById('cps'),
                clickUpgradeButton: document.getElementById('clickUpgradeButton'),
                cpsUpgradeButton: document.getElementById('cpsUpgradeButton'),
                multiplierUpgradeButton: document.getElementById('multiplierUpgradeButton'),
                clickUpgradeCostDisplay: document.getElementById('clickUpgradeCost'),
                cpsUpgradeCostDisplay: document.getElementById('cpsUpgradeCost'),
                multiplierUpgradeCostDisplay: document.getElementById('multiplierUpgradeCost'),
                clickUpgradeCountDisplay: document.getElementById('clickUpgradeCount'),
                cpsUpgradeCountDisplay: document.getElementById('cpsUpgradeCount'),
                multiplierUpgradeCountDisplay: document.getElementById('multiplierUpgradeCount')
            };

            function updateDisplays() {
                elements.cookieCountDisplay.textContent = cookieCount;
                elements.allTimeCookiesDisplay.textContent = allTimeCookies;
                elements.cookiesPerClickDisplay.textContent = cookiesPerClick * multiplier;
                elements.cpsDisplay.textContent = cookiesPerSecond * multiplier;
                elements.clickUpgradeCostDisplay.textContent = clickUpgradeCost;
                elements.cpsUpgradeCostDisplay.textContent = cpsUpgradeCost;
                elements.multiplierUpgradeCostDisplay.textContent = multiplierUpgradeCost;
                elements.clickUpgradeCountDisplay.textContent = clickUpgradesPurchased;
                elements.cpsUpgradeCountDisplay.textContent = cpsUpgradesPurchased;
                elements.multiplierUpgradeCountDisplay.textContent = multiplierUpgradesPurchased;
            }

            function earnCookies() {
                let cookiesToAdd = cookiesPerClick * multiplier;
                cookieCount += cookiesToAdd;
                allTimeCookies += cookiesToAdd;
                updateDisplays();
            }

            function upgradeCookiesPerClick() {
                if (cookieCount >= clickUpgradeCost) {
                    cookieCount -= clickUpgradeCost;
                    cookiesPerClick += clickIncrement;
                    clickUpgradeCost = Math.floor(clickUpgradeCost * 1.5);
                    clickUpgradesPurchased++;
                    updateDisplays();
                }
            }

            function upgradeCPS() {
                if (cookieCount >= cpsUpgradeCost) {
                    cookieCount -= cpsUpgradeCost;
                    cookiesPerSecond += cpsIncrement;
                    cpsUpgradeCost = Math.floor(cpsUpgradeCost * 1.5);
                    cpsUpgradesPurchased++;
                    updateDisplays();
                }
            }

            function upgradeMultiplier() {
                if (cookieCount >= multiplierUpgradeCost) {
                    cookieCount -= multiplierUpgradeCost;
                    multiplier += multiplierMultiplier;
                    multiplierUpgradeCost = Math.floor(multiplierUpgradeCost * 3);
                    multiplierUpgradesPurchased++;
                    updateDisplays();
                }
            }

            elements.cookieButton.addEventListener('click', earnCookies);
            elements.clickUpgradeButton.addEventListener('click', upgradeCookiesPerClick);
            elements.cpsUpgradeButton.addEventListener('click', upgradeCPS);
            elements.multiplierUpgradeButton.addEventListener('click', upgradeMultiplier);

            setInterval(() => {
                let passiveCookies = cookiesPerSecond * multiplier;
                cookieCount += passiveCookies;
                allTimeCookies += passiveCookies; // Add passive cookies to all-time cookies
                updateDisplays();
            }, 1000);

            updateDisplays();
        });
    </script>
</body>
</html>
