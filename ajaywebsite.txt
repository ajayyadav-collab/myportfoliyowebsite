<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ajay Yadav - Cloud & DevOps Learner</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        
        :root {
            --primary: #3498db;
            --dark: #2c3e50;
            --light: #ecf0f1;
            --accent: #e74c3c;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 20px;
            /* ensure header content sits above animations */
            position: relative;
            z-index: 2;
        }
        
        header {
            background: linear-gradient(135deg, var(--dark), var(--primary));
            color: white;
            padding: 60px 0 80px;
            text-align: center;
            clip-path: polygon(0 0, 100% 0, 100% 85%, 0 100%);
            position: relative;
            overflow: hidden;
        }

        /* --- lightweight particles canvas behind everything --- */
        #hero-canvas {
            position: absolute;
            inset: 0;
            width: 100%;
            height: 100%;
            z-index: 0; /* behind the decorative overlay + content */
            pointer-events: none;
        }
        
        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none"><path fill="rgba(255,255,255,0.05)" d="M0,0 L100,0 L100,100 L0,100 Z" /></svg>');
            background-size: cover;
            animation: pulse 15s infinite alternate;
            z-index: 1; /* above canvas, below content */
        }
        
        @keyframes pulse {
            0% { opacity: 0.05; }
            100% { opacity: 0.1; }
        }
        
        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 20px;
            animation: float 6s ease-in-out infinite;
            position: relative;
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            position: relative;
            display: inline-block;
        }
        
        h1::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 50px;
            height: 3px;
            background-color: var(--accent);
        }
        
        .tagline {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 20px;
        }

        /* --- typing effect added (non-intrusive) --- */
        .tagline .typing {
            border-right: 2px solid rgba(255,255,255,0.85);
            white-space: nowrap;
            overflow: hidden;
            display: inline-block;
            width: 0;
            animation: typing 3.5s steps(28, end) forwards, blink .75s step-end infinite;
        }
        @keyframes typing { from { width: 0 } to { width: 260px } }
        @keyframes blink { 50% { border-color: transparent } }
        
        .contact-info {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 8px;
            background: rgba(255,255,255,0.1);
            padding: 8px 15px;
            border-radius: 30px;
            transition: all 0.3s ease;
        }
        
        .contact-item:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-3px);
        }
        
        .contact-item i {
            font-size: 1.2rem;
        }
        
        section {
            padding: 60px 0;
            background: white;
            margin: -40px 20px 0;
            border-radius: 10px;
            box-shadow: 0 5px 25px rgba(0,0,0,0.05);
            position: relative;
            z-index: 1;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 40px;
            color: var(--dark);
            position: relative;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background-color: var(--primary);
        }
        
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .card {
            background: white;
            border-radius: 8px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: all 0.3s ease;
            border-left: 4px solid var(--primary);
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .card h3 {
            color: var(--primary);
            margin-bottom: 15px;
            font-size: 1.3rem;
        }
        
        .card h4 {
            color: var(--dark);
            margin-bottom: 10px;
            font-weight: 600;
        }
        
        .card p {
            color: #666;
            margin-bottom: 5px;
        }
        
        .card .date {
            font-size: 0.9rem;
            color: #999;
            margin-bottom: 15px;
        }
        
        .skills-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }
        
        .skill {
            background: var(--light);
            padding: 8px 15px;
            border-radius: 30px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }
        
        .skill:hover {
            background: var(--primary);
            color: white;
            transform: scale(1.05);
        }
        
        .certificate-item {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }
        
        .certificate-item:last-child {
            border-bottom: none;
            margin-bottom: 0;
            padding-bottom: 0;
        }
        
        .certificate-icon {
            width: 50px;
            height: 50px;
            background: var(--light);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
            font-size: 1.5rem;
            flex-shrink: 0;
        }
        
        .training-sessions {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .session-item {
            background: var(--light);
            padding: 12px 15px;
            border-radius: 5px;
            font-size: 0.9rem;
            position: relative;
            padding-left: 25px;
        }
        
        .session-item::before {
            content: '→';
            position: absolute;
            left: 10px;
            color: var(--primary);
        }
        
        footer {
            background: var(--dark);
            color: white;
            text-align: center;
            padding: 30px 0;
            margin-top: 40px;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }
        
        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255,255,255,0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;
        }
        
        .social-link:hover {
            background: var(--primary);
            transform: translateY(-3px);
        }
        
        @media (max-width: 768px) {
            header {
                padding: 40px 0 60px;
            }
            
            .contact-info {
                flex-direction: column;
                align-items: center;
            }
            
            section {
                margin: -30px 10px 0;
            }
        }
        
        /* Animation classes */
        .fade-in {
            animation: fadeIn 1s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .delay-1 { animation-delay: 0.2s; }
        .delay-2 { animation-delay: 0.4s; }
        .delay-3 { animation-delay: 0.6s; }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
    <header>
        <!-- particles canvas (added) -->
        <canvas id="hero-canvas"></canvas>

        <div class="container">
            <!-- ✅ your profile image kept as-is -->
            <img src="https://storage.googleapis.com/ajayyadavajayyadav/ajay123.jpeg" alt="Ajay Yadav" class="profile-img">
            <h1>AJAY YADAV</h1>
            <!-- ✅ tagline with typing effect (added span only) -->
            <p class="tagline"><span class="typing">Cloud & DevOps Learner</span></p>
            <div class="contact-info">
                <a href="https://mail.google.com/mail/?view=cm&fs=1&to=ay815515@gmai.com" target="_blank" class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <span>ay815515@gmail.com</span>
                </a>
                <a href="websiteto:www.ajayyadav.co.in" class="contact-item">
                    <i class="fas fa-globe"></i>
                    <span>www.ajayyadav.co.in</span>
                </a>          
                <!-- Removed phone number as per request -->
            </div>
        </div>
    </header>
    
    <section class="fade-in">
        <div class="container">
            <h2 class="section-title">Career Objective</h2>
            <div class="card fade-in delay-1">
                <p>To leverage my foundational skills in Linux, AWS Cloud, Shell Scripting and Docker to contribute effectively to cloud infrastructure and DevOps projects. Seeking an opportunity to grow my expertise in deploying scalable solutions, automating workflows, and optimizing system performance while delivering secure and efficient cloud-based services.</p>
            </div>
        </div>
    </section>
    
    <section class="fade-in delay-2">
        <div class="container">
            <h2 class="section-title">Topics covered in the training</h2>
            <div class="card fade-in delay-1">
                <h3><u>Linux Topics Covered</u></h3>
                <div class="training-sessions">
                    <div class="session-item">Basic Linux commands</div>
                    <div class="session-item">User & Group management</div>
                    <div class="session-item">Permission (file & Directory)</div>
                    <div class="session-item">Tar file (compress, compress file view, extract), SCP </div>
                    <div class="session-item">Package Management</div>
                    <div class="session-item">View running process, Cronjob</div>
                </div>
                
                <h3> <u>AWS Topics Covered</u> </h3>
                <div class="training-sessions">
                    <div class="session-item">Networking</div>
                    <div class="session-item">Firewall, Firewall commands, logs</div>
                    <div class="session-item">DNS server</div>
                    <div class="session-item">Web server</div>
                    <div class="session-item">CUT & SED command, echo command</div>
                    <div class="session-item">Shells scripting</div>
                    <div class="session-item">Disc Management</div>
                    <div class="session-item">EC2 (Elastic compute cloud)</div>
                    <div class="session-item">Window Server and Linux server connect</div>
                    <div class="session-item">Volume and Snapshot</div>
                    <div class="session-item">Load balancer and Auto scaling</div>
                    <div class="session-item">Simple Storage Service (S3)</div>
                    <div class="session-item">S3, Bucket versioning, S3 advantage and disadvantage</div>
                    <div class="session-item">IAM users & IAM role</div>
                    <div class="session-item">Live DNS implementation, Route 53, Nameserver, Database</div>
                    <div class="session-item">RDS, Database backup</div>
                    <div class="session-item">Caching solutions, Elastic Cache service, DMS, VPC</div>
                    <div class="session-item">VPC, NAT Gateway, Elastic IP</div>
                    <div class="session-item">Use of VPC, VPC Peering, Network Network ACLs</div>
                    <div class="session-item">AWS SQS, SWF, Application Load balancer</div>
                    <div class="session-item">SNS, CDN, Cloud watch, Billing & Cont management, Cloud front, Edge locations</div>
                </div>
                
                <h3><u>Docker Topics Covered</u></h3>
                <div class="training-sessions">
                    <div class="session-item">Docker Basic</div>
                    <div class="session-item">Docker commands (run,ps,images,start, stop, attach, exec,logs, commit, stats, save, rm, rmi, load)</div>
                    <div class="session-item">Docker commands (tag, login, logout, push, inspect)</div>
                    <div class="session-item"> Dockerfile, Port mapping, Docker build</div>
                    <div class="session-item">Volume Management in Docker</div>
                    <div class="session-item">Docker compose</div>
                </div>
                
                <h3><u> Kubernetes Topics Covered</u></h3>
                <div class="training-sessions">
                    <div class="session-item">Kubernetes Informations</div>
                    <div class="session-item">Pod creation, Delete</div>
                    <div class="session-item">Node Selector, Replicaset, Service, namespace</div>
                    <div class="session-item"> Node affinity, readiness probe, liveness probe </div>
                    <div class="session-item">Upgrades and Volumes in Kubernetes, NFS server, PV & PVC</div>
                    <div class="session-item">Database in Kubernetes, Configmap, Secret</div>
                    <div class="session-item">Ingress</div>
                    <div class="session-item">Security in Kubernetes, Role & RoleBinding</div>
                    <div class="session-item">ClusterRole, ClusterRoleBinding, Metrix Server, Dashboard</div>
                </div>
                
            </div>
        </div>
    </section>
 
    <section class="fade-in delay-1">
        <div class="container">
            <h2 class="section-title">Education</h2>
            <div class="grid-container">
                <div class="card fade-in delay-1">
                    <h3>B.tech (Agri. Engineering)</h3>
                    <p>College of Agricultural Engineering & Technology, Anand Agricultural University, Godhra</p>
                    <p class="date">CGPA: 7.079</p>
                </div>
                <div class="card fade-in delay-2">
                    <h3>H.S.C - 2019</h3>
                    <p>St. Xavier's High School, Gamdi Anand</p>
                    <p class="date">Percentage: 57.69%</p>
                </div>
                <div class="card fade-in delay-3">
                    <h3>S.S.C - 2017</h3>
                    <p>Shree Saraswati Shishu Mandir, Dakor</p>
                    <p class="date">Percentage: 79.83%</p>
                </div>
            </div>
        </div>
    </section>
    
    <section class="fade-in delay-2">
        <div class="container">
            <h2 class="section-title">Skills</h2>
            <div class="card fade-in delay-1">
                <div class="skills-container">
                    <span class="skill">AWS Cloud Computing</span>
                    <span class="skill">Linux Administration</span>
                    <span class="skill">Shell Scripting</span>
                    <span class="skill">Docker Basics</span>
                    <span class="skill">Red Hat Certified</span>
                    <span class="skill">Kubernetes Basics</span>
                </div>
            </div>
        </div>
    </section>
    
    <section class="fade-in delay-2">
        <div class="container">
            <h2 class="section-title">Professional Experience</h2>
            <div class="grid-container">
                <div class="card fade-in delay-1">
                    <h3>Cloud & DevOps Learner</h3>
                    <p class="date">01/2025 – Present</p>
                    <p>Currently undergoing training in Linux, AWS, Docker, Kubernetes, Git</p>
                </div>
                <div class="card fade-in delay-2">
                    <h3>Officer in Netafim Irrigation</h3>
                    <p class="date">04/2024 – Present</p>
                    <p>Professional experience in irrigation systems and technology.</p>
                </div>
                <div class="card fade-in delay-3">
                    <h3>Design Engineer in Kothari Irrigation</h3>
                    <p class="date">07/2023 – 03/2024</p>
                    <p>Worked as a design engineer in irrigation systems.</p>
                </div>
            </div>
        </div>
    </section>
    
    <section class="fade-in delay-3">
        <div class="container">
            <h2 class="section-title">Certificates</h2>
            <div class="card fade-in delay-1">
                <div class="certificate-item">
                    <div class="certificate-icon">
                        <i class="fab fa-docker"></i>
                    </div>
                    <div>
                        <h4>Docker Container Program</h4>
                        <p>Completed Docker training program by DevOps TechLab</p>
                        <p class="date">June 10, 2025</p>
                    </div>
                </div>
                <div class="certificate-item">
                    <div class="certificate-icon">
                        <i class="fab fa-aws"></i>
                    </div>
                    <div>
                        <h4>AWS Certified Solutions Architect - Associate</h4>
                        <p>Certification in AWS cloud architecture</p>
                    </div>
                </div>
                <div class="certificate-item">
                    <div class="certificate-icon">
                        <i class="fas fa-certificate"></i>
                    </div>
                    <div>
                        <h4>Red Hat Certified Engineer</h4>
                        <p>Professional certification in Linux system administration</p>
                    </div>
                </div>
                
                <div class="certificate-item">
                    <div class="certificate-icon">
                        <i class="fas fa-laptop-code"></i>
                    </div>
                    <div>
                        <h4>Course on Computer Concept (CCC)</h4>
                        <p>Certificate course in computer fundamentals</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <footer class="fade-in delay-3">
        <div class="container">
            <p>&copy; 2025 Ajay Yadav. All rights reserved.</p>
            <div class="social-links">
                <a href="https://www.linkedin.com/in/ajayyadav-collab/" class="social-link" target="_blank">
                    <i class="fab fa-linkedin-in"></i>
                </a>
                <a href="https://github.com/ajayyadav-collab" class="social-link" target="_blank"> 
                    <i class="fab fa-github"></i>
                </a>
                <a href="https://www.instagram.com/ajay_1_yadav?igsh=MTEyNW5oY3F1YWM3dQ==" class="social-link" target="_blank"> 
                    <i class="fab fa-instagram"></i>
                </a>
            </div>
        </div>
    </footer>

    <!-- tiny particles script (no external library) -->
    <script>
      (function () {
        const canvas = document.getElementById('hero-canvas');
        const ctx = canvas.getContext('2d');
        let w, h, particles;

        function resize() {
          w = canvas.width = canvas.offsetWidth = canvas.parentElement.clientWidth;
          h = canvas.height = canvas.offsetHeight = canvas.parentElement.clientHeight;
          init();
        }

        function init() {
          const count = Math.min(100, Math.floor(w * h / 18000)); // responsive density
          particles = Array.from({ length: count }).map(() => ({
            x: Math.random() * w,
            y: Math.random() * h,
            vx: (Math.random() - 0.5) * 0.6,
            vy: (Math.random() - 0.5) * 0.6,
            r: Math.random() * 1.8 + 0.7
          }));
        }

        function step() {
          ctx.clearRect(0, 0, w, h);
          // draw links
          for (let i = 0; i < particles.length; i++) {
            for (let j = i + 1; j < particles.length; j++) {
              const a = particles[i], b = particles[j];
              const dx = a.x - b.x, dy = a.y - b.y;
              const dist = Math.hypot(dx, dy);
              if (dist < 120) {
                ctx.globalAlpha = 1 - dist / 120;
                ctx.beginPath();
                ctx.moveTo(a.x, a.y);
                ctx.lineTo(b.x, b.y);
                ctx.strokeStyle = 'rgba(255,255,255,0.6)';
                ctx.lineWidth = 0.5;
                ctx.stroke();
              }
            }
          }
          ctx.globalAlpha = 1;

          // draw nodes & move
          particles.forEach(p => {
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
            ctx.fillStyle = 'rgba(255,255,255,0.9)';
            ctx.fill();

            p.x += p.vx;
            p.y += p.vy;
            // bounce on edges
            if (p.x < 0 || p.x > w) p.vx *= -1;
            if (p.y < 0 || p.y > h) p.vy *= -1;
          });

          requestAnimationFrame(step);
        }

        window.addEventListener('resize', resize);
        resize();
        step();
      })();
    </script>
</body>
</html>
