<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EUR/USD Pattern Scanner</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- TradingView Lightweight Charts -->
    <script src="https://unpkg.com/lightweight-charts/dist/lightweight-charts.standalone.production.js"></script>
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Custom styles -->
    <style>
        .pattern-indicator {
            animation: pulse 2s infinite;
        }
        @keyframes pulse {
            0% { opacity: 0.6; }
            50% { opacity: 1; }
            100% { opacity: 0.6; }
        }
        .chart-container {
            height: 500px;
        }
        .pattern-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }
        .pattern-card {
            transition: all 0.3s ease;
        }
    </style>
</head>
<body class="bg-gray-100 text-gray-800">
    <div class="container mx-auto px-4 py-8">
        <!-- Header -->
        <header class="mb-8">
            <div class="flex justify-between items-center">
                <div>
                    <h1 class="text-3xl font-bold text-blue-600">EUR/USD Pattern Scanner</h1>
                    <p class="text-gray-600">Free live market analysis with automatic pattern recognition</p>
                </div>
                <div class="flex items-center space-x-4">
                    <div class="bg-white p-3 rounded-lg shadow">
                        <div class="flex items-center">
                            <span class="font-bold mr-2">EUR/USD:</span>
                            <span id="current-price" class="text-green-600 font-bold">1.0854</span>
                            <span id="price-change" class="ml-2 text-green-600">+0.12%</span>
                        </div>
                    </div>
                    <div id="market-status" class="bg-green-100 text-green-800 px-3 py-2 rounded-full text-sm">
                        Market Open
                    </div>
                </div>
            </div>
        </header>

        <!-- Main Content -->
        <main>
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Chart Section -->
                <div class="lg:col-span-2 bg-white rounded-xl shadow-md overflow-hidden">
                    <div class="p-4 border-b border-gray-200 flex justify-between items-center">
                        <h2 class="text-xl font-semibold">Live EUR/USD Chart</h2>
                        <div class="flex space-x-2">
                            <select id="timeframe" class="border rounded px-3 py-1 text-sm">
                                <option value="1">1 Minute</option>
                                <option value="5">5 Minutes</option>
                                <option value="15" selected>15 Minutes</option>
                                <option value="60">1 Hour</option>
                                <option value="240">4 Hours</option>
                                <option value="1D">Daily</option>
                            </select>
                            <button id="fullscreen-btn" class="bg-gray-100 hover:bg-gray-200 p-2 rounded">
                                <i class="fas fa-expand"></i>
                            </button>
                        </div>
                    </div>
                    <div id="chart" class="chart-container"></div>
                </div>

                <!-- Patterns Section -->
                <div class="bg-white rounded-xl shadow-md overflow-hidden">
                    <div class="p-4 border-b border-gray-200">
                        <h2 class="text-xl font-semibold">Detected Patterns</h2>
                        <p class="text-sm text-gray-500">Automatically identified chart patterns</p>
                    </div>
                    <div class="p-4 space-y-4" id="patterns-container">
                        <!-- Patterns will be added here dynamically -->
                        <div class="text-center py-10 text-gray-400" id="loading-patterns">
                            <i class="fas fa-spinner fa-spin fa-2x mb-2"></i>
                            <p>Scanning for patterns...</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Market Info Section -->
            <div class="mt-6 grid grid-cols-1 md:grid-cols-3 gap-4">
                <div class="bg-white p-4 rounded-lg shadow">
                    <div class="flex justify-between items-center">
                        <h3 class="font-semibold">Support Levels</h3>
                        <i class="fas fa-shield-alt text-blue-500"></i>
                    </div>
                    <ul class="mt-3 space-y-2" id="support-levels">
                        <li class="flex justify-between"><span>1.0820</span> <span class="text-green-500">Strong</span></li>
                        <li class="flex justify-between"><span>1.0785</span> <span class="text-yellow-500">Medium</span></li>
                        <li class="flex justify-between"><span>1.0750</span> <span class="text-red-500">Weak</span></li>
                    </ul>
                </div>
                <div class="bg-white p-4 rounded-lg shadow">
                    <div class="flex justify-between items-center">
                        <h3 class="font-semibold">Resistance Levels</h3>
                        <i class="fas fa-chart-line text-red-500"></i>
                    </div>
                    <ul class="mt-3 space-y-2" id="resistance-levels">
                        <li class="flex justify-between"><span>1.0880</span> <span class="text-green-500">Strong</span></li>
                        <li class="flex justify-between"><span>1.0915</span> <span class="text-yellow-500">Medium</span></li>
                        <li class="flex justify-between"><span>1.0950</span> <span class="text-red-500">Weak</span></li>
                    </ul>
                </div>
                <div class="bg-white p-4 rounded-lg shadow">
                    <div class="flex justify-between items-center">
                        <h3 class="font-semibold">Market Sentiment</h3>
                        <i class="fas fa-balance-scale text-purple-500"></i>
                    </div>
                    <div class="mt-3">
                        <div class="flex justify-between mb-1">
                            <span>Bullish</span>
                            <span>62%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-2.5">
                            <div class="bg-green-600 h-2.5 rounded-full" style="width: 62%"></div>
                        </div>
                        <div class="flex justify-between mt-3 mb-1">
                            <span>Bearish</span>
                            <span>38%</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-2.5">
                            <div class="bg-red-600 h-2.5 rounded-full" style="width: 38%"></div>
                        </div>
                    </div>
                </div>
            </div>
        </main>

        <!-- Footer -->
        <footer class="mt-12 pt-6 border-t border-gray-200 text-center text-gray-500 text-sm">
            <p>Disclaimer: This is a free tool for educational purposes only. Market data may be delayed.</p>
            <p class="mt-2">© 2023 EUR/USD Pattern Scanner. All data provided by free APIs.</p>
        </footer>
    </div>

    <script>
        // Initialize chart
        document.addEventListener('DOMContentLoaded', function() {
            // Chart setup
            const chartContainer = document.getElementById('chart');
            const chart = LightweightCharts.createChart(chartContainer, {
                layout: {
                    backgroundColor: '#FFFFFF',
                    textColor: '#333',
                },
                grid: {
                    vertLines: {
                        color: '#eee',
                    },
                    horzLines: {
                        color: '#eee',
                    },
                },
                crosshair: {
                    mode: LightweightCharts.CrosshairMode.Normal,
                },
                rightPriceScale: {
                    borderVisible: false,
                },
                timeScale: {
                    borderVisible: false,
                },
            });

            const candleSeries = chart.addCandlestickSeries({
                upColor: '#26a69a',
                downColor: '#ef5350',
                borderVisible: false,
                wickUpColor: '#26a69a',
                wickDownColor: '#ef5350',
            });

            // Mock data - in a real app, you would fetch this from an API
            function generateMockData() {
                const now = new Date();
                const data = [];
                let previousClose = 1.0850;
                
                for (let i = 0; i < 100; i++) {
                    const time = new Date(now);
                    time.setMinutes(time.getMinutes() - i * 15);
                    
                    const open = previousClose;
                    const high = open + (Math.random() * 0.0015);
                    const low = open - (Math.random() * 0.0015);
                    const close = low + (Math.random() * (high - low));
                    
                    data.push({
                        time: Math.floor(time.getTime() / 1000),
                        open: open,
                        high: high,
                        low: low,
                        close: close,
                    });
                    
                    previousClose = close;
                }
                
                return data.reverse();
            }

            const initialData = generateMockData();
            candleSeries.setData(initialData);

            // Simulate live updates
            setInterval(() => {
                const lastCandle = initialData[initialData.length - 1];
                const newTime = lastCandle.time + 900; // Add 15 minutes
                
                const open = lastCandle.close;
                const high = open + (Math.random() * 0.0010);
                const low = open - (Math.random() * 0.0010);
                const close = low + (Math.random() * (high - low));
                
                const newCandle = {
                    time: newTime,
                    open: open,
                    high: high,
                    low: low,
                    close: close,
                };
                
                initialData.push(newCandle);
                candleSeries.update(newCandle);
                
                // Update current price display
                document.getElementById('current-price').textContent = close.toFixed(4);
                const change = ((close - open) / open * 100).toFixed(2);
                const changeElement = document.getElementById('price-change');
                changeElement.textContent = `${change > 0 ? '+' : ''}${change}%`;
                changeElement.className = change >= 0 ? 'ml-2 text-green-600' : 'ml-2 text-red-600';
                
            }, 3000);

            // Timeframe selector
            document.getElementById('timeframe').addEventListener('change', function() {
                // In a real app, this would fetch new data for the selected timeframe
                console.log('Timeframe changed to:', this.value);
            });

            // Fullscreen button
            document.getElementById('fullscreen-btn').addEventListener('click', function() {
                if (chartContainer.requestFullscreen) {
                    chartContainer.requestFullscreen();
                } else if (chartContainer.webkitRequestFullscreen) {
                    chartContainer.webkitRequestFullscreen();
                } else if (chartContainer.msRequestFullscreen) {
                    chartContainer.msRequestFullscreen();
                }
            });

            // Simulate pattern detection
            setTimeout(() => {
                document.getElementById('loading-patterns').remove();
                
                const patterns = [
                    {
                        name: "Head and Shoulders",
                        confidence: "High",
                        direction: "Bearish",
                        timeframe: "4H",
                        since: "2 hours ago"
                    },
                    {
                        name: "Double Bottom",
                        confidence: "Medium",
                        direction: "Bullish",
                        timeframe: "1H",
                        since: "45 minutes ago"
                    },
                    {
                        name: "Ascending Triangle",
                        confidence: "High",
                        direction: "Bullish",
                        timeframe: "Daily",
                        since: "3 days ago"
                    },
                    {
                        name: "Bullish Flag",
                        confidence: "Low",
                        direction: "Bullish",
                        timeframe: "15M",
                        since: "30 minutes ago"
                    }
                ];
                
                const patternsContainer = document.getElementById('patterns-container');
                
                patterns.forEach(pattern => {
                    const card = document.createElement('div');
                    card.className = `pattern-card bg-white border rounded-lg p-4 ${
                        pattern.direction === 'Bullish' ? 'border-green-200' : 'border-red-200'
                    }`;
                    
                    card.innerHTML = `
                        <div class="flex justify-between items-start">
                            <div>
                                <h3 class="font-bold text-lg">${pattern.name}</h3>
                                <div class="flex items-center mt-1">
                                    <span class="text-sm ${
                                        pattern.direction === 'Bullish' ? 'text-green-600' : 'text-red-600'
                                    }">
                                        ${pattern.direction}
                                    </span>
                                    <span class="mx-2 text-gray-400">|</span>
                                    <span class="text-sm text-gray-600">${pattern.timeframe}</span>
                                </div>
                            </div>
                            <span class="px-2 py-1 text-xs rounded-full ${
                                pattern.confidence === 'High' ? 'bg-green-100 text-green-800' : 
                                pattern.confidence === 'Medium' ? 'bg-yellow-100 text-yellow-800' : 'bg-red-100 text-red-800'
                            }">
                                ${pattern.confidence} confidence
                            </span>
                        </div>
                        <div class="mt-3 flex justify-between items-center text-sm text-gray-500">
                            <span>Detected ${pattern.since}</span>
                            <button class="text-blue-500 hover:text-blue-700">
                                <i class="fas fa-chart-line"></i> View
                            </button>
                        </div>
                    `;
                    
                    patternsContainer.appendChild(card);
                });
                
                // Add pattern indicators to chart
                // This is a simplified version - in a real app you would calculate these properly
                const markers = [
                    {
                        time: initialData[initialData.length - 15].time,
                        position: 'belowBar',
                        color: '#f68410',
                        shape: 'arrowUp',
                        text: 'Double Bottom'
                    },
                    {
                        time: initialData[initialData.length - 5].time,
                        position: 'aboveBar',
                        color: '#ef5350',
                        shape: 'arrowDown',
                        text: 'Head & Shoulders'
                    }
                ];
                
                candleSeries.setMarkers(markers);
                
            }, 2000);
        });
    </script>
</body>
</html>
