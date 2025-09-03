<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fernando Valenzuela | Especialista en Redes y Ciberseguridad</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@300;400;500&family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        /* === PALETA DE COLORES (Opción A: Ciber-Verde y Neón) === */
        :root {
            --primary: #0a192f;
            --secondary: #112240;
            --accent: #64ffda;
            --accent-dark: #52d1b8;
            --light: #ccd6f6;
            --gray: #8892b0;
            --lightest: #e6f1ff;
        }
        
        /* === RESET Y ESTILOS BASE === */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        html { scroll-behavior: smooth; }
        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--primary);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        h1, h2, h3, h4, h5, h6 {
            font-family: 'Roboto Mono', monospace;
            color: var(--lightest);
            margin-bottom: 1rem;
        }
        
        a { text-decoration: none; color: inherit; }
        img { max-width: 100%; height: auto; display: block; }
        
        .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
        .section { padding: 100px 0; }
        
        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
            padding-bottom: 15px;
            color: var(--lightest);
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--accent);
            border-radius: 2px;
        }
        
        /* === COMPONENTES REUTILIZABLES === */
        .btn {
            display: inline-block;
            background: transparent;
            color: var(--accent);
            padding: 12px 28px;
            border: 1px solid var(--accent);
            border-radius: 4px;
            text-decoration: none;
            font-size: 1rem;
            font-weight: 500;
            transition: all 0.3s;
            cursor: pointer;
            font-family: 'Roboto Mono', monospace;
        }
        
        .btn:hover {
            background: rgba(100, 255, 218, 0.1);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }
        
        .btn-filled {
            background: var(--accent);
            color: var(--primary);
        }
        
        .btn-filled:hover {
            background: var(--accent-dark);
            color: var(--primary);
        }

        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }
        
        .fade-in.visible { opacity: 1; transform: translateY(0); }
        
        /* === HEADER & NAVIGATION === */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            background-color: rgba(10, 25, 47, 0.85);
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        
        header.scrolled { box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2); padding: 10px 0; }
        
        nav { display: flex; justify-content: space-between; align-items: center; padding: 20px 0; transition: padding 0.3s ease;}
        
        .logo { font-family: 'Roboto Mono', monospace; font-size: 1.8rem; font-weight: 700; color: var(--accent); display: flex; align-items: center; }
        .logo i { margin-right: 10px; }
        
        .nav-links { display: flex; list-style: none; }
        .nav-links li { margin-left: 30px; }
        .nav-links a { color: var(--light); font-weight: 500; transition: color 0.3s; position: relative; font-size: 1rem; }
        .nav-links a::after { content: ''; position: absolute; width: 0; height: 2px; bottom: -5px; left: 0; background-color: var(--accent); transition: width 0.3s; }
        .nav-links a:hover { color: var(--accent); }
        .nav-links a:hover::after { width: 100%; }
        
        .menu-btn { display: none; font-size: 1.5rem; color: var(--light); cursor: pointer; }
        
        /* === HERO SECTION === */
        .hero { min-height: 100vh; display: flex; align-items: center; }
        .hero-content { max-width: 800px; }
        .hero-subtitle { font-size: 1.2rem; color: var(--accent); margin-bottom: 1rem; font-family: 'Roboto Mono', monospace; }
        .hero-title { font-size: 3.5rem; margin-bottom: 1.5rem; line-height: 1.2; color: var(--lightest); }
        .hero-description { font-size: 1.2rem; margin-bottom: 2.5rem; color: var(--gray); }
        .hero-actions { display: flex; gap: 15px; flex-wrap: wrap; }
        
        /* === ABOUT SECTION === */
        .about { background-color: var(--secondary); }
        .about-content { display: grid; grid-template-columns: 3fr 2fr; gap: 50px; align-items: center; }
        .about-text h3 { font-size: 1.8rem; margin-bottom: 20px; color: var(--accent); }
        .about-text p { margin-bottom: 15px; font-size: 1.1rem; color: var(--gray); }
        .about-image { position: relative; }
        .about-image img { border-radius: 10px; box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3); filter: grayscale(50%) contrast(1.1); }
        .about-image::after { content: ''; position: absolute; top: 20px; left: 20px; right: -20px; bottom: -20px; border: 2px solid var(--accent); border-radius: 10px; z-index: -1; transition: all 0.3s ease; }
        .about-image:hover::after { transform: translate(-8px, -8px); }
        
        /* === SKILLS SECTION === */
        .skills-container { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; }
        
        .skill-category {
            background: var(--secondary);
            padding: 30px;
            border-radius: 10px;
            border: 1px solid #1f335c;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .skill-category:hover { transform: translateY(-8px); box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2); }
        .skill-category h3 { font-size: 1.4em; margin: 0 0 25px 0; color: var(--lightest); display: flex; align-items: center; gap: 12px; }
        .skill-category h3 i { color: var(--accent); }
        
        .tech-stack { display: flex; flex-wrap: wrap; gap: 12px; }
        
        .tech-item {
            background-color: var(--primary);
            color: var(--gray);
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        
        .tech-item:hover { background-color: var(--accent); color: var(--primary); }
        
        /* === PROJECTS SECTION === */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px;
        }

        .project-card {
            background: var(--secondary);
            border-radius: 8px;
            padding: 30px;
            border: 1px solid transparent; /* Borde invisible para mantener tamaño en hover */
            transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
        }

        .project-card:hover {
            transform: translateY(-8px);
            border-color: var(--accent);
            box-shadow: 0 10px 30px -15px rgba(0, 0, 0, 0.7);
        }

        .project-top {
            margin-bottom: 25px;
        }

        .project-category {
            font-family: 'Roboto Mono', monospace;
            font-size: 0.9rem;
            color: var(--gray);
        }

        .project-info {
            display: flex;
            flex-direction: column;
            flex-grow: 1; /* Esto empuja los links al fondo */
        }

        .project-info h3 {
            color: var(--lightest);
            margin-bottom: 20px;
            font-size: 1.6rem;
            line-height: 1.3;
        }

        .project-info p {
            color: var(--gray);
            margin-bottom: 25px;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: auto; /* Empuja las etiquetas hacia abajo si la descripción es corta */
            margin-bottom: 25px;
        }

        .project-tag {
            background: rgba(100, 255, 218, 0.1);
            color: var(--accent);
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-family: 'Roboto Mono', monospace;
            font-weight: 500;
        }

        .project-links {
            display: flex;
            gap: 25px;
        }

        .project-link {
            display: inline-flex;
            align-items: center;
            color: var(--light);
            font-weight: 500;
            transition: color 0.3s;
            font-family: 'Roboto Mono', monospace;
        }

        .project-link:hover {
            color: var(--accent);
        }

        .project-link i {
            margin-right: 8px;
            font-size: 1.1rem;
        }
        /* === CERTIFICATIONS SECTION === */
        .certifications { background-color: var(--secondary); }
        .certs-container { display: flex; flex-wrap: wrap; justify-content: center; gap: 30px; margin-top: 50px; }
        .cert-card { background: var(--primary); padding: 25px; border-radius: 10px; width: 250px; text-align: center; border: 1px solid #1f335c; transition: all 0.3s; }
        .cert-card:hover { transform: translateY(-10px); box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2); }
        .cert-icon { font-size: 3rem; color: var(--accent); margin-bottom: 15px; }
        .cert-title { font-size: 1.2rem; margin-bottom: 10px; color: var(--lightest); }
        .cert-org { color: var(--gray); font-size: 0.9rem; }
        
        /* === PROJECTS SECTION (revisado) === */
        .projects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(350px, 1fr)); gap: 30px; }
        .project-card { background: var(--secondary); border-radius: 10px; overflow: hidden; border: 1px solid #1f335c; transition: transform 0.3s; display: flex; flex-direction: column; }
        .project-card:hover { transform: translateY(-10px); box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2); }
        .project-image { height: 200px; overflow: hidden; }
        .project-image img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.4s ease; }
        .project-card:hover .project-image img { transform: scale(1.05); }
        .project-info { padding: 25px; flex-grow: 1; display: flex; flex-direction: column; }
        .project-info h3 { color: var(--lightest); margin-bottom: 15px; font-size: 1.5rem; }
        .project-info p { color: var(--gray); margin-bottom: 20px; flex-grow: 1; }
        .project-tags { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 20px; }
        .project-tag { background: rgba(100, 255, 218, 0.1); color: var(--accent); padding: 5px 12px; border-radius: 20px
