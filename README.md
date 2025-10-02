# c<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>JKS Group Vertical Sidebar Platform</title>
<style>
  body {
    background: #20242b;
    color: #fff;
    font-family: 'Segoe UI', Arial, sans-serif;
    margin: 0;
    padding: 0;
  }
  header {
    background: #141b29;
    text-align: center;
    padding: 20px 0;
    font-weight: 700;
    font-size: 2rem;
    color: #00e1ff;
    letter-spacing: 2px;
    text-shadow: 0 0 20px #0fccfccc;
  }
  #container {
    display: flex;
    min-height: 90vh;
  }
  #sidebar {
    width: 220px;
    background: #141b29;
    border-right: 3px solid #00e1ff;
    display: flex;
    flex-direction: column;
  }
  .sidebar-item {
    padding: 18px 12px;
    border-bottom: 1px solid #0fccfcaa;
    text-align: center;
    font-weight: 600;
    cursor: pointer;
    transition: 0.3s;
    user-select: none;
  }
  .sidebar-item:hover, .sidebar-item.active {
    background: #00e1ff;
    color: #141b29;
    font-weight: 700;
  }
  #content {
    flex: 1;
    padding: 20px;
  }
  .section-title {
    font-size: 1.75rem;
    color: #ffe27f;
    text-align: center;
    text-shadow: 0 0 22px #ffe27fbb;
    margin-bottom: 24px;
  }
  .service-list, .events-categories {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 26px 30px;
  }
  .service-card, .category-card {
    background: #23273b;
    border: 3px solid #ffe27f;
    border-radius: 14px;
    font-weight: 700;
    font-size: 1.15em;
    padding: 36px 18px;
    color: #ffe27f;
    cursor: pointer;
    text-align: center;
    transition: 0.3s;
    box-shadow: 0 0 18px 3px #fff68d88;
    user-select: none;
  }
  .service-card:hover, .category-card:hover {
    background: #ffe27f;
    color: #141a2b;
    box-shadow: 0 0 38px 12px #0fccfac9, 0 8px 26px #246124af;
    font-weight: 900;
    transform: scale(1.07);
  }
  form.contact-form {
    max-width: 450px;
    margin: 10px auto 40px;
    padding: 25px 26px;
    background: #18253f;
    border-radius: 12px;
    border: 2px solid #00e1ff99;
    color: #b9d6ffcc;
  }
  form.contact-form label {
    display: block;
    font-weight: 700;
    margin-bottom: 8px;
    color: #94b7ff;
  }
  form.contact-form input, form.contact-form textarea, form.contact-form select {
    width: 100%;
    padding: 12px 15px;
    font-size: 15px;
    margin-bottom: 20px;
    border-radius: 9px;
    border: 1.5px solid #59abfb;
    background: #0a1a34;
    color: #b8d5ff;
    resize: vertical;
    outline: none;
  }
  form.contact-form input:focus, form.contact-form textarea:focus, form.contact-form select:focus {
    border-color: #00bfff;
    background: #104983;
  }
  form.contact-form button {
    width: 100%;
    padding: 15px 0;
    font-weight: 900;
    font-size: 1.2em;
    color: #192b3a;
    background: #00e1ff;
    border: none;
    border-radius: 14px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  form.contact-form button:hover {
    background: #3de1ff;
  }
  .back-btn {
    background: #ffe27f;
    border-radius: 14px;
    padding: 14px 60px;
    font-weight: 900;
    font-size: 1.15em;
    color: #222a39;
    cursor: pointer;
    margin: 0 auto;
    display: block;
    border: 3px solid #ffe27f;
    box-shadow: 2px 2px 25px #f7ef878f;
    user-select: none;
    transition: all 0.3s ease;
  }
  .back-btn:hover {
    background: #00e1ff;
    border-color: #00e1ff;
    color: #fff;
    box-shadow: 0 0 36px 14px #00e1ffcc;
  }
  #map {
    height: 450px;
    border-radius: 14px;
    border: 3px solid #00e1ff94;
    box-shadow: 0 0 38px 20px #00e1ff55;
    margin: 0 auto 40px;
    max-width: 640px;
  }
  video#video {
    max-width: 100%;
    border-radius: 14px;
    border: 2px solid #00e1ff8f;
    margin-top: 20px;
  }
  #photoOutput img {
    max-width: 320px;
    border-radius: 12px;
  }
  @media (max-width: 900px) {
    #container {
      flex-direction: column;
    }
    #sidebar {
      width: 100%;
      flex-direction: row;
      overflow-x: auto;
      border-right: none;
      border-bottom: 3px solid #00e1ff;
    }
    .sidebar-item {
      flex: none;
      padding: 12px 18px;
      font-weight: 600;
    }
  }
</style>
</head>
<body>
<header>JKS Group of Business</header>
<div id="container">
  <aside id="sidebar"></aside>
  <section id="content">
    <section id="dashboard" class="dashboard"></section>

    <section id="profile" style="display:none;">
      <h2 class="section-title">Profile</h2>
      <form class="contact-form">
        <label>Name:</label>
        <input id="profileName" type="text" />
        <label>Email:</label>
        <input id="profileEmail" type="email" />
        <label>Phone:</label>
        <input id="profilePhone" type="tel" />
        <label>Address:</label>
        <textarea id="profileAddress" rows="3"></textarea>
        <button type="button" onclick="alert('Profile saved!')">Save</button>
      </form>
      <button class="back-btn" onclick="showContent('dashboard')">Back to Dashboard</button>
    </section>

    <section id="wallet" style="display:none;">
      <h2 class="section-title">Wallet</h2>
      <p>Balance: ₹<span id="walletBalance">10000</span></p>
      <form class="contact-form" onsubmit="addMoney(event)">
        <label>Add Money:</label>
        <input id="addMoneyInput" type="number" min="1" required />
        <button type="submit">Add Funds</button>
      </form>
      <button class="back-btn" onclick="showContent('dashboard')">Back to Dashboard</button>
    </section>

    <section id="orders" style="display:none;">
      <h2 class="section-title">Orders</h2>
      <table style="width: 100%; border-collapse: collapse; background: #1c2238; color: #fff; border-radius: 8px; overflow: hidden;">
        <thead><tr><th style="padding: 14px;">Order ID</th><th>Product / Service</th><th>Status</th></tr></thead>
        <tbody>
          <tr><td>001</td><td>Pizza</td><td style="color: #3eff9d;">Delivered</td></tr>
          <tr><td>002</td><td>Car Wash</td><td style="color: #ffe27f;">Pending</td></tr>
          <tr><td>003</td><td>Loan Enquiry</td><td style="color: #0bcfff;">In Progress</td></tr>
        </tbody>
      </table>
      <button class="back-btn" onclick="showContent('dashboard')">Back to Dashboard</button>
    </section>

    <section id="serviceView" style="display:none; flex-direction:column; align-items:center;">
      <h2 class="section-title" id="serviceTitle"></h2>
      <div class="service-list" id="serviceList"></div>
      <form class="contact-form" id="contactForm" style="display:none;">
        <label>Name:</label>
        <input type="text" id="userName" required />
        <label>Mobile:</label>
        <input type="tel" id="userPhone" maxlength="10" pattern="[6-9][0-9]{9}" required />
        <label>Message:</label>
        <textarea id="userMessage" rows="4" required></textarea>
        <button type="button" onclick="submitContactForm()">Submit WhatsApp</button>
        <button type="button" class="back-btn" onclick="backToServiceList()">Back to Services</button>
      </form>
      <button class="back-btn" onclick="showContent('dashboard')">Back to Dashboard</button>
    </section>

    <section id="eventsView" style="display:none; flex-direction: column; align-items: center;">
      <h2 class="section-title" id="eventsCategoryTitle"></h2>
      <div class="events-categories" id="eventsCategories"></div>
      <div class="service-list" id="eventsServiceList"></div>
      <form class="contact-form" id="eventContactForm" style="display:none;">
        <label>Name:</label>
        <input id="eventsUserName" type="text" required />
        <label>Mobile:</label>
        <input id="eventsUserPhone" type="tel" maxlength="10" pattern="[6-9][0-9]{9}" required />
        <div id="customFields"></div>
        <label>Message:</label>
        <textarea id="eventsUserMessage" rows="4" required></textarea>
        <button type="button" onclick="submitEventsForm()">Submit WhatsApp</button>
        <button type="button" class="back-btn" onclick="backToEventsCategory()">Back</button>
      </form>
      <button class="back-btn" onclick="showContent('dashboard')">Back to Dashboard</button>
    </section>

    <section id="ecomView" style="display:none;">
      <h2 class="section-title">My E-commerce</h2>
      <nav style="margin-bottom: 18px;">
        <button onclick="openEcomCategory('Groceries')">Groceries</button>
        <button onclick="openEcomCategory('Food')">Food</button>
        <button onclick="openEcomCategory('Pharmacy')">Pharmacy</button>
        <button onclick="showContent('camera')" style="margin-left: 30px;">Camera</button>
        <button onclick="showContent('maps')">Google Maps</button>
      </nav>
      <div class="service-list" id="ecomServiceList"></div>
      <form id="ecomOrderForm" class="contact-form" style="display:none;">
        <h3 id="ecomOrderTitle"></h3>
        <label>Name:</label>
        <input name="name" type="text" required />
        <label>Mobile:</label>
        <input name="phone" type="tel" maxlength="10" pattern="[6-9][0-9]{9}" required />
        <label>Order Details:</label>
        <textarea name="orderDetails" rows="3" required></textarea>
        <label>Delivery Address:</label>
        <textarea name="address" required></textarea>
        <button type="submit">Order WhatsApp</button>
        <button type="button" class="back-btn" onclick="backToEcomServices()">Back</button>
      </form>
      <button class="back-btn" onclick="showContent('dashboard')">Back to Dashboard</button>
    </section>

    <section id="camera" style="display:none; text-align:center;">
      <h2 class="section-title">Camera</h2>
      <video id="video" autoplay muted playsinline></video>
      <div style="margin:20px;">
        <button onclick="switchCamera()">Switch Camera</button>
        <button onclick="capturePhoto()">Capture Photo</button>
      </div>
      <canvas id="canvas" style="display:none;"></canvas>
      <div id="photoOutput" style="margin-top:20px;"></div>
      <button class="back-btn" onclick="showContent('dashboard')">Back</button>
    </section>

    <section id="maps" style="display:none; text-align:center;">
      <h2 class="section-title">Google Maps</h2>
      <div id="map"></div>
      <button class="back-btn" onclick="showContent('dashboard')">Back</button>
    </section>
  </section>
</div>

<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY&callback=initMap" async defer></script>
<script>
const folders = [
  {id: 'dashboard', label: 'Dashboard'},
  {id: 'profile', label: 'Profile'},
  {id: 'wallet', label: 'Wallet'},
  {id: 'orders', label: 'Orders'},
  {id: 'serviceView', label: 'Services'},
  {id: 'eventsView', label: 'Events & Catering'},
  {id: 'ecomView', label: 'My E-commerce'},
  {id: 'camera', label: 'Camera'},
  {id: 'maps', label: 'Google Maps'}
];
const modulesServices = {
  courier: ['Courier Booking', 'Ride Booking', 'Tracking', 'Support', 'Rental Vehicles'],
  job: ['Job Search', 'Post Resume', 'Local Jobs', 'Non-Local Jobs', 'PG & Hostel', 'Services Marketplace'],
  tours: ['Tour Bookings', 'Custom & Regular Tours', 'Stay Booking', 'Vehicle Booking', 'Train/Bus/Flight Tickets'],
  realestate: ['Buy', 'Sell', 'Rent', 'Key Services', 'Construction', 'Industry'],
  investment: ['Gold', 'Silver', 'Real Estate', 'Business Opportunity', 'Mutual Funds'],
  loans: ['Loan Enquiry', 'Car Insurance', 'Bike Insurance', 'Housing Loans', 'Personal Loans', 'Health Insurance'],
  home: ['CC Camera Installation', 'Computer Repair', 'Car Wash', 'Mobile Repair', 'Chef Services', 'Bouncers', 'Bike Mechanic', 'Car Mechanic', 'Electrician', 'Painter', 'Plumber', 'Driver']
};
const ecom = {
  Groceries: ['Milk', 'Meat', 'Fruits', 'Vegetables', 'Flowers', 'Others'],
  Food: ['Biriyani', 'Tiffins', 'Ice Cream', 'Pizza', 'Burgers', 'Rolls'],
  Pharmacy: ['Medicines', 'Health Products', 'Supplements', 'Care Products']
};
const eventsCategories = {
  package: [
    {name: "Silver", amount: "50k - 160k"},
    {name: "Gold", amount: "150k - 300k"},
    {name: "Diamond", amount: "500k - 5M"},
    {name: "Platinum", amount: "500k - 800k"}
  ],
  customized: [
    "Decoration", "Catering", "Photography & Videography", "Anchor & Actors", "DJ & Singers", "Guest House", "Chocolate & Cake", "Games & Entertainment", "Jewellery", "Invitation Cards", "Vehicles", "Return Gifts", "Makeup Artist", "Mehandi Artist", "Clothing & Accessories"
  ],
  premium: [
    "Decoration", "Catering", "Photography & Videography", "Anchor & Actors", "DJ & Singers", "Guest House", "Chocolate & Cake", "Games & Entertainment", "Jewellery", "Invitation Cards", "Vehicles", "Return Gifts", "Makeup Artist", "Mehandi Artist", "Clothing & Accessories"
  ]
};
let currentModule = 'dashboard';
let currentService = '';
let currentEventCategory = '';
let currentEventService = '';
let currentEcomCategory = '';

function updateSidebar() {
  let sidebar = document.getElementById('sidebar');
  sidebar.innerHTML = '';
  folders.forEach(({id, label}) => {
    let div = document.createElement('div');
    div.className = 'sidebar-item' + (id === currentModule ? ' active' : '');
    div.textContent = label;
    div.onclick = () => {
      if(id === 'dashboard') showContent('dashboard');
      else if(id === 'profile') showContent('profile');
      else if(id === 'wallet') showContent('wallet');
      else if(id === 'orders') showContent('orders');
      else if(id === 'serviceView') showContent('serviceView');
      else if(id === 'eventsView') showContent('eventsView');
      else if(id === 'ecomView') showContent('ecomView');
      else if(id === 'camera') showContent('camera');
      else if(id === 'maps') showContent('maps');
    };
    sidebar.appendChild(div);
  });
}

function showContent(sectionId) {
  currentModule = sectionId;
  updateSidebar();
  document.querySelectorAll('#content > section').forEach(s => { s.style.display = 'none'; });
  document.getElementById(sectionId).style.display = 'block';
  if(sectionId === 'dashboard'){
    renderDashboard();
  } else if(sectionId === 'eventsView'){
    openEventsDashboard();
  } else if(sectionId === 'ecomView'){
    openEcomDashboard();
  }
  if(sectionId === 'camera'){
    startCamera();
  }
  if(sectionId === 'maps' && !window.mapLoaded) {
    initMap();
    window.mapLoaded = true;
  }
}

function renderDashboard() {
  let container = document.getElementById('dashboard');
  container.innerHTML = '';
  folders.forEach(({id, label}) => {
    if(['dashboard', 'profile', 'wallet', 'orders', 'serviceView', 'eventsView', 'ecomView', 'camera', 'maps'].includes(id)) return;
    let div = document.createElement('div');
    div.className = 'folder-card';
    div.textContent = label;
    div.onclick = () => openModule(id);
    container.appendChild(div);
  });
}

function openModule(id) {
  if(id === 'events'){
    showContent('eventsView');
  } else if(id === 'ecommerce'){
    showContent('ecomView');
  } else {
    currentModule = id;
    let services = moduleServices[id] || [];
    let serviceList = document.getElementById('serviceList');
    serviceList.innerHTML = '';
    services.forEach(service => {
      let div = document.createElement('div');
      div.className = 'service-card';
      div.textContent = service;
      div.onclick = () => openContactForm(service);
      serviceList.appendChild(div);
    });
    document.getElementById('serviceTitle').innerText = folders.find(f => f.id === id)?.label || '';
    showContent('serviceView');
  }
}

function openContactForm(service) {
  currentService = service;
  document.getElementById('serviceList').style.display = 'none';
  let form = document.getElementById('contactForm');
  form.style.display = 'block';
  document.getElementById('contactTitle').innerText = 'Contact for ' + service;
  clearInputs(['userName', 'userPhone', 'userMessage']);
}

function backToServiceList() {
  document.getElementById('contactForm').style.display = 'none';
  document.getElementById('serviceList').style.display = 'grid';
}

function submitContactForm() {
  const name = document.getElementById('userName').value.trim();
  const phone = document.getElementById('userPhone').value.trim();
  const msg = document.getElementById('userMessage').value.trim();
  if(!name || !phone || !msg) {
    alert('Fill all fields');
    return;
  }
  const waMsg = `Name: ${encodeURIComponent(name)}%0APhone: ${encodeURIComponent(phone)}%0AService: ${encodeURIComponent(currentService)}%0AMessage: ${encodeURIComponent(msg)}`;
  window.open(`https://wa.me/8977143043?text=${waMsg}`, '_blank');
}

function clearInputs(ids){
  ids.forEach(id => { let e=document.getElementById(id); if(e) e.value=''; });
}

// Events functions
function openEventsDashboard(){
  currentEventCategory = '';
  currentEventService = '';
  const catsDiv = document.getElementById('eventsCategories');
  catsDiv.innerHTML = '';
  ['package','customized','premium'].forEach(cat=>{
    let d=document.createElement('div');
    d.className='category-card';
    d.textContent = cat.charAt(0).toUpperCase()+cat.slice(1);
    d.onclick=()=>openEventsCategory(cat);
    catsDiv.appendChild(d);
  });
  document.getElementById('eventsServiceList').innerHTML = '';
  document.getElementById('eventContactForm').style.display = 'none';
  document.getElementById('eventsCategoryTitle').innerText = 'Events & Catering Categories';
}

function openEventsCategory(cat){
  currentEventCategory = cat;
  currentEventService = '';
  const svcList = document.getElementById('eventsServiceList');
  document.getElementById('eventContactForm').style.display = 'none';
  svcList.style.display = 'grid';
  svcList.innerHTML = '';
  if(cat == 'package'){
    [
      { name: "Silver", amount: "50k - 160k" },
      { name: "Gold", amount: "150k - 300k" },
      { name: "Diamond", amount: "500k - 5M" },
      { name: "Platinum", amount: "500k - 800k" }
    ].forEach(pkg => {
      let d=document.createElement('div');
      d.className='service-card';
      d.textContent = `${pkg.name} (${pkg.amount})`;
      d.onclick=()=>openEventContactForm(pkg.name, cat);
      svcList.appendChild(d);
    });
  }else{
    const services = cat==='customized' ? [
      "Decoration", "Catering", "Photography & Videography", "Anchor & Actors", "DJ & Singers", "Guest House",
      "Chocolate & Cake", "Games & Entertainment", "Jewellery", "Invitation Cards", "Vehicles", "Return Gifts",
      "Makeup Artist", "Mehandi Artist", "Clothing & Accessories"
    ] : [
      "Decoration", "Catering", "Photography & Videography", "Anchor & Actors", "DJ & Singers", "Guest House",
      "Chocolate & Cake", "Games & Entertainment", "Jewellery", "Invitation Cards", "Vehicles", "Return Gifts",
      "Makeup Artist", "Mehandi Artist", "Clothing & Accessories"
    ];
    services.forEach(svc=>{
      let d=document.createElement('div');
      d.className='service-card';
      d.textContent=svc;
      d.onclick=()=>openEventContactForm(svc, cat);
      svcList.appendChild(d);
    });
  }
  document.getElementById('eventsCategoryTitle').innerText = cat.charAt(0).toUpperCase()+cat.slice(1) + ' Services';
}

function openEventContactForm(service, category){
  currentEventService = service;
  document.getElementById('eventsServiceList').style.display = 'none';
  let form = document.getElementById('eventContactForm');
  form.style.display = 'block';
  document.getElementById('eventsContactTitle').innerText = 'Contact for ' + service;
  document.getElementById('eventsUserName').value = '';
  document.getElementById('eventsUserPhone').value = '';
  document.getElementById('eventsUserMessage').value = '';
  const customFields = document.getElementById('customFields');
  if(category === 'customized'){
    customFields.innerHTML = `
      <label>Budget:</label>
      <select id="eventsBudget" required>
        <option value="">Select Budget</option>
        <option>10k to 50k</option>
        <option>50k to 1L</option>
        <option>1L to 5L</option>
        <option>5L to 10L</option>
        <option>Above 10L</option>
      </select>
      <label>Capacity:</label>
      <select id="eventsCapacity" required>
        <option value="">Select Capacity</option>
        <option>5-30 people</option>
        <option>30-60 people</option>
        <option>60-90 people</option>
        <option>90-130 people</option>
        <option>Above 130 people</option>
      </select>`;
  } else {
    customFields.innerHTML = '';
  }
}

function backToEventsCategory(){
  document.getElementById('eventContactForm').style.display = 'none';
  document.getElementById('eventsServiceList').style.display = 'grid';
}

function submitEventsForm(){
  const name = document.getElementById('eventsUserName').value.trim();
  const phone = document.getElementById('eventsUserPhone').value.trim();
  const message = document.getElementById('eventsUserMessage').value.trim();
  let budget = '';
  let capacity = '';
  if(currentEventCategory === 'customized'){
    budget = document.getElementById('eventsBudget').value;
    capacity = document.getElementById('eventsCapacity').value;
    if(!budget || !capacity){
      alert('Please select budget and capacity');
      return;
    }
  }
  if(!name || !phone || !message){
    alert('Please fill all fields');
    return;
  }
  let whatsappMsg = `Name: ${encodeURIComponent(name)}%0APhone: ${encodeURIComponent(phone)}%0AService: ${encodeURIComponent(currentEventService)}%0ACategory: ${encodeURIComponent(currentEventCategory)}%0AMessage: ${encodeURIComponent(message)}`;
  if(budget) whatsappMsg += `%0ABudget: ${encodeURIComponent(budget)}`;
  if(capacity) whatsappMsg += `%0ACapacity: ${encodeURIComponent(capacity)}`;
  window.open(`https://wa.me/8977143043?text=${whatsappMsg}`, '_blank');
}

// E-commerce functions
function openEcomDashboard(){
  currentEcomCategory = '';
  document.getElementById('dashboard').style.display = 'none';
  document.getElementById('serviceView').style.display = 'none';
  document.getElementById('eventsView').style.display = 'none';
  document.getElementById('ecomView').style.display = 'block';
  document.getElementById('ecomServiceList').innerHTML = '';
  document.getElementById('ecomOrderForm').style.display = 'none';
}

function openEcomCategory(cat){
  currentEcomCategory = cat;
  const svcList = document.getElementById('ecomServiceList');
  svcList.innerHTML = '';
  (ecom[cat]||[]).forEach(service=>{
    const d = document.createElement('div');
    d.className = 'service-card';
    d.textContent = service;
    d.onclick = () => openEcomOrderForm(cat, service);
    svcList.appendChild(d);
  });
  document.getElementById('ecomOrderForm').style.display = 'none';
  svcList.style.display = 'grid';
}

function openEcomOrderForm(cat, service){
  document.getElementById('ecomOrderForm').style.display = 'block';
  document.getElementById('ecomOrderTitle').textContent = `Order ${service} in ${cat}`;
  document.getElementById('ecomOrderForm').onsubmit = e => submitOrderForm(e, cat, service);
}

function backToEcomServices(){
  document.getElementById('ecomOrderForm').style.display = 'none';
}

function submitOrderForm(e, cat, service){
  e.preventDefault();
  const form = e.target;
  const name = form.name.value.trim();
  const phone = form.phone.value.trim();
  const details = form.orderDetails.value.trim();
  const address = form.address.value.trim();
  if(!name || !phone || !details || !address){
    alert('Please fill all order form fields');
    return;
  }
  let msg = `Order from JKS E-commerce%0ACategory: ${cat}%0AProduct: ${service}%0AName: ${name}%0APhone: ${phone}%0AOrder Details: ${details}%0AAddress: ${address}`;
  window.open(`https://wa.me/8977143043?text=${encodeURIComponent(msg)}`, '_blank');
}

// Camera
let currentStream = null;
let usingFrontCamera = true;

function startCamera(){
  const video = document.getElementById('video');
  if(currentStream) currentStream.getTracks().forEach(t => t.stop());
  navigator.mediaDevices.getUserMedia({video: {facingMode: usingFrontCamera ? 'user' : 'environment'}}).then(stream=>{
    currentStream=stream;
    video.srcObject=stream;
    video.play();
  }).catch(()=>alert('Camera access denied'));
}
function switchCamera(){
  usingFrontCamera=!usingFrontCamera;
  startCamera();
}
function capturePhoto(){
  const video=document.getElementById('video');
  const canvas=document.getElementById('canvas');
  canvas.width=video.videoWidth;
  canvas.height=video.videoHeight;
  const ctx=canvas.getContext('2d');
  ctx.drawImage(video,0,0);
  const dataUrl=canvas.toDataURL();
  document.getElementById('photoOutput').innerHTML=`<img src="${dataUrl}" style="max-width:320px;border-radius:12px;">`;
}

// Wallet
function addMoney(e){
  e.preventDefault();
  const input=document.getElementById('addMoneyInput');
  const amount=parseFloat(input.value);
  if(isNaN(amount)||amount<=0){
    alert('Enter valid amount');
    return;
  }
  const balElem=document.getElementById('walletBalance');
  let balance=parseFloat(balElem.textContent);
  balance+=amount;
  balElem.textContent=balance.toFixed(2);
  alert(`₹${amount.toFixed(2)} added to wallet.`);
  input.value='';
}

// Google Maps
function initMap(){
  new google.maps.Map(document.getElementById('map'), {
    center:{lat:17.3850,lng:78.4867},
    zoom:13
  });
}

document.addEventListener('DOMContentLoaded', ()=>{
  updateSidebar();
  showContent('dashboard');
});
</script>
</body>
</html>
