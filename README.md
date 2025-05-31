# aprovadodigital<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aprovado Digital - Plataforma de Cursos para Concursos</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #27ae60;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8f9fa;
            color: #333;
        }
        
        .navbar {
            background: linear-gradient(135deg, var(--primary) 0%, var(--dark) 100%);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .hero-section {
            background: linear-gradient(rgba(44, 62, 80, 0.8), rgba(44, 62, 80, 0.8)), url('https://images.unsplash.com/photo-1523240795612-9a054b0db644?ixlib=rb-4.0.3&auto=format&fit=crop&w=1950&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            padding: 100px 0;
        }
        
        .feature-card {
            transition: all 0.3s ease;
            border: none;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
            height: 100%;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }
        
        .course-card {
            border-radius: 10px;
            overflow: hidden;
            transition: all 0.3s ease;
            height: 100%;
        }
        
        .course-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }
        
        .admin-panel {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1000;
            width: 350px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            overflow: hidden;
            display: none;
        }
        
        .admin-header {
            background: linear-gradient(135deg, var(--primary) 0%, var(--dark) 100%);
            color: white;
            padding: 15px;
            cursor: pointer;
        }
        
        .admin-content {
            padding: 20px;
            max-height: 400px;
            overflow-y: auto;
        }
        
        .tab-content {
            padding: 20px 0;
        }
        
        .stats-card {
            border-radius: 10px;
            padding: 20px;
            color: white;
            text-align: center;
            margin-bottom: 20px;
        }
        
        .stat-1 { background: linear-gradient(135deg, #3498db, #2980b9); }
        .stat-2 { background: linear-gradient(135deg, #2ecc71, #27ae60); }
        .stat-3 { background: linear-gradient(135deg, #e74c3c, #c0392b); }
        .stat-4 { background: linear-gradient(135deg, #9b59b6, #8e44ad); }
        
        .testimonial-card {
            border-left: 4px solid var(--secondary);
            background: white;
            padding: 20px;
            border-radius: 0 8px 8px 0;
            margin-bottom: 20px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
        }
        
        .footer {
            background: var(--dark);
            color: white;
            padding: 50px 0 20px;
        }
        
        .footer a {
            color: #ddd;
            text-decoration: none;
        }
        
        .footer a:hover {
            color: white;
        }
        
        .social-icon {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(255,255,255,0.1);
            display: inline-flex;
            align-items: center;
            justify-content: center;
            margin-right: 10px;
            transition: all 0.3s ease;
        }
        
        .social-icon:hover {
            background: var(--secondary);
            transform: translateY(-3px);
        }
        
        .btn-primary {
            background: var(--secondary);
            border: none;
            padding: 10px 25px;
            border-radius: 30px;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .btn-primary:hover {
            background: #2980b9;
            transform: translateY(-2px);
        }
        
        .btn-accent {
            background: var(--accent);
            color: white;
            border: none;
            padding: 10px 25px;
            border-radius: 30px;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .btn-accent:hover {
            background: #c0392b;
            transform: translateY(-2px);
        }
        
        .section-title {
            position: relative;
            padding-bottom: 15px;
            margin-bottom: 30px;
        }
        
        .section-title:after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--secondary);
            border-radius: 2px;
        }
        
        .form-control {
            border-radius: 8px;
            padding: 12px 15px;
            border: 1px solid #ddd;
        }
        
        .form-control:focus {
            border-color: var(--secondary);
            box-shadow: 0 0 0 0.25rem rgba(52, 152, 219, 0.25);
        }
    </style>
</head>
<body>
    <!-- Admin Panel -->
    <div class="admin-panel" id="adminPanel">
        <div class="admin-header" id="adminToggle">
            <h5 class="mb-0"><i class="fas fa-cog me-2"></i> Painel Administrativo</h5>
        </div>
        <div class="admin-content">
            <ul class="nav nav-tabs" id="adminTabs" role="tablist">
                <li class="nav-item" role="presentation">
                    <button class="nav-link active" id="courses-tab" data-bs-toggle="tab" data-bs-target="#courses" type="button" role="tab">Cursos</button>
                </li>
                <li class="nav-item" role="presentation">
                    <button class="nav-link" id="students-tab" data-bs-toggle="tab" data-bs-target="#students" type="button" role="tab">Alunos</button>
                </li>
                <li class="nav-item" role="presentation">
                    <button class="nav-link" id="ebooks-tab" data-bs-toggle="tab" data-bs-target="#ebooks" type="button" role="tab">E-books</button>
                </li>
                <li class="nav-item" role="presentation">
                    <button class="nav-link" id="sheets-tab" data-bs-toggle="tab" data-bs-target="#sheets" type="button" role="tab">Planilhas</button>
                </li>
            </ul>
            
            <div class="tab-content" id="adminTabContent">
                <div class="tab-pane fade show active" id="courses" role="tabpanel">
                    <div class="mb-3">
                        <label class="form-label">Nome do Curso</label>
                        <input type="text" class="form-control" id="courseName">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Área</label>
                        <select class="form-select" id="courseArea">
                            <option value="INSS">INSS</option>
                            <option value="PRF">PRF</option>
                            <option value="PF">PF</option>
                            <option value="Marítimo">Marítimo</option>
                            <option value="Outros">Outros</option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Preço (R$)</label>
                        <input type="number" class="form-control" id="coursePrice">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Descrição</label>
                        <textarea class="form-control" id="courseDescription" rows="3"></textarea>
                    </div>
                    <button class="btn btn-primary w-100" id="addCourseBtn">Adicionar Curso</button>
                </div>
                
                <div class="tab-pane fade" id="students" role="tabpanel">
                    <div class="mb-3">
                        <label class="form-label">Nome do Aluno</label>
                        <input type="text" class="form-control" id="studentName">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">E-mail</label>
                        <input type="email" class="form-control" id="studentEmail">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Curso</label>
                        <select class="form-select" id="studentCourse">
                            <option value="Curso INSS">Curso Preparatório INSS</option>
                            <option value="Curso PRF">Curso Preparatório PRF</option>
                            <option value="Curso PF">Curso Preparatório PF</option>
                        </select>
                    </div>
                    <button class="btn btn-primary w-100" id="addStudentBtn">Adicionar Aluno</button>
                </div>
                
                <div class="tab-pane fade" id="ebooks" role="tabpanel">
                    <div class="mb-3">
                        <label class="form-label">Título do E-book</label>
                        <input type="text" class="form-control" id="ebookTitle">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Categoria</label>
                        <select class="form-select" id="ebookCategory">
                            <option value="Concursos">Concursos Públicos</option>
                            <option value="Estudo">Métodos de Estudo</option>
                            <option value="Direito">Direito</option>
                        </select>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Preço (R$)</label>
                        <input type="number" class="form-control" id="ebookPrice">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Arquivo</label>
                        <input type="file" class="form-control" id="ebookFile">
                    </div>
                    <button class="btn btn-primary w-100" id="addEbookBtn">Adicionar E-book</button>
                </div>
                
                <div class="tab-pane fade" id="sheets" role="tabpanel">
                    <div class="mb-3">
                        <label class="form-label">Nome da Planilha</label>
                        <input type="text" class="form-control" id="sheetName">
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Descrição</label>
                        <textarea class="form-control" id="sheetDescription" rows="2"></textarea>
                    </div>
                    <div class="mb-3">
                        <label class="form-label">Arquivo (Excel/PDF)</label>
                        <input type="file" class="form-control" id="sheetFile">
                    </div>
                    <button class="btn btn-primary w-100" id="addSheetBtn">Adicionar Planilha</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Navigation -->
    <nav class="navbar navbar-expand-lg navbar-dark sticky-top">
        <div class="container">
            <a class="navbar-brand" href="#">
                <i class="fas fa-graduation-cap me-2"></i>
                <span class="fw-bold">APROVADO DIGITAL</span>
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link active" href="#">Início</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#cursos">Cursos</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#ebooks">E-books</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#planilhas">Planilhas</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#depoimentos">Depoimentos</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#contato">Contato</a>
                    </li>
                    <li class="nav-item ms-lg-3">
                        <a class="btn btn-outline-light" href="#"><i class="fas fa-user me-2"></i>Área do Aluno</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero-section">
        <div class="container text-center">
            <div class="row justify-content-center">
                <div class="col-lg-8">
                    <h1 class="display-4 fw-bold mb-4">Sua Aprovação em Concursos Públicos Começa Aqui</h1>
                    <p class="lead mb-5">Plataforma completa com cursos preparatórios, e-books exclusivos e planilhas inteligentes para você conquistar a sua vaga</p>
                    <div class="d-flex justify-content-center gap-3">
                        <a href="#cursos" class="btn btn-primary btn-lg px-4 py-3">Conheça Nossos Cursos</a>
                        <a href="#planilhas" class="btn btn-outline-light btn-lg px-4 py-3">Planilhas Gratuitas</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Features -->
    <section class="py-5 bg-white">
        <div class="container">
            <div class="row g-4">
                <div class="col-md-4">
                    <div class="feature-card text-center p-4">
                        <div class="icon bg-primary bg-gradient text-white rounded-circle d-inline-flex align-items-center justify-content-center p-3 mb-4">
                            <i class="fas fa-book fa-2x"></i>
                        </div>
                        <h4 class="mb-3">E-books Exclusivos</h4>
                        <p class="text-muted">Conteúdo de alta qualidade desenvolvido por especialistas em concursos públicos.</p>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="feature-card text-center p-4">
                        <div class="icon bg-success bg-gradient text-white rounded-circle d-inline-flex align-items-center justify-content-center p-3 mb-4">
                            <i class="fas fa-users fa-2x"></i>
                        </div>
                        <h4 class="mb-3">Gestão de Alunos</h4>
                        <p class="text-muted">Controle completo dos alunos, desempenho e progresso nos estudos.</p>
                    </div>
                </div>
                <div class="col-md-4">
                    <div class="feature-card text-center p-4">
                        <div class="icon bg-info bg-gradient text-white rounded-circle d-inline-flex align-items-center justify-content-center p-3 mb-4">
                            <i class="fas fa-file-excel fa-2x"></i>
                        </div>
                        <h4 class="mb-3">Planilhas Inteligentes</h4>
                        <p class="text-muted">Ferramentas para organização de estudos, controle financeiro e planejamento.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Courses -->
    <section id="cursos" class="py-5 bg-light">
        <div class="container">
            <div class="text-center mb-5">
                <h2 class="section-title d-inline-block">Nossos Cursos</h2>
                <p class="text-muted">Cursos completos com tudo que você precisa para ser aprovado</p>
            </div>
            
            <div class="row g-4">
                <div class="col-lg-4 col-md-6">
                    <div class="course-card card h-100">
                        <div class="card-header bg-primary text-white">
                            <h5 class="mb-0">Preparatório INSS</h5>
                        </div>
                        <div class="card-body">
                            <p class="text-muted">Curso completo para o concurso do Instituto Nacional do Seguro Social</p>
                            <ul class="list-group list-group-flush mb-3">
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Videoaulas atualizadas</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Materiais em PDF</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Simulados semanais</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Suporte de professores</li>
                            </ul>
                        </div>
                        <div class="card-footer bg-transparent">
                            <div class="d-flex justify-content-between align-items-center">
                                <h5 class="mb-0 text-success">R$ 297,00</h5>
                                <button class="btn btn-primary">Inscreva-se</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-lg-4 col-md-6">
                    <div class="course-card card h-100">
                        <div class="card-header bg-success text-white">
                            <h5 class="mb-0">Preparatório PRF</h5>
                        </div>
                        <div class="card-body">
                            <p class="text-muted">Curso completo para Polícia Rodoviária Federal</p>
                            <ul class="list-group list-group-flush mb-3">
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Videoaulas atualizadas</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Materiais em PDF</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Simulados semanais</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Suporte de professores</li>
                            </ul>
                        </div>
                        <div class="card-footer bg-transparent">
                            <div class="d-flex justify-content-between align-items-center">
                                <h5 class="mb-0 text-success">R$ 347,00</h5>
                                <button class="btn btn-primary">Inscreva-se</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-lg-4 col-md-6">
                    <div class="course-card card h-100">
                        <div class="card-header bg-danger text-white">
                            <h5 class="mb-0">Preparatório PF</h5>
                        </div>
                        <div class="card-body">
                            <p class="text-muted">Curso completo para Polícia Federal</p>
                            <ul class="list-group list-group-flush mb-3">
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Videoaulas atualizadas</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Materiais em PDF</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Simulados semanais</li>
                                <li class="list-group-item"><i class="fas fa-check text-success me-2"></i> Suporte de professores</li>
                            </ul>
                        </div>
                        <div class="card-footer bg-transparent">
                            <div class="d-flex justify-content-between align-items-center">
                                <h5 class="mb-0 text-success">R$ 397,00</h5>
                                <button class="btn btn-primary">Inscreva-se</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="text-center mt-5">
                <a href="#" class="btn btn-outline-primary">Ver Todos os Cursos</a>
            </div>
        </div>
    </section>

    <!-- E-books -->
    <section id="ebooks" class="py-5 bg-white">
        <div class="container">
            <div class="text-center mb-5">
                <h2 class="section-title d-inline-block">Nossos E-books</h2>
                <p class="text-muted">Conteúdo exclusivo para impulsionar seus estudos</p>
            </div>
            
            <div class="row g-4">
                <div class="col-md-4">
                    <div class="card h-100">
                        <img src="https://images.unsplash.com/photo-1495446815901-a7297e633e8d?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" class="card-img-top" alt="E-book">
                        <div class="card-body">
                            <h5 class="card-title">Guia Completo de Direito Previdenciário</h5>
                            <p class="card-text">Tudo que você precisa saber para dominar as questões de previdência em concursos.</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <h5 class="mb-0 text-success">R$ 47,90</h5>
                                <button class="btn btn-sm btn-outline-primary">Comprar</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4">
                    <div class="card h-100">
                        <img src="https://images.unsplash.com/photo-1512820790803-83ca734da794?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" class="card-img-top" alt="E-book">
                        <div class="card-body">
                            <h5 class="card-title">Mapas Mentais para Concursos</h5>
                            <p class="card-text">Técnicas avançadas de memorização para acelerar seu aprendizado.</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <h5 class="mb-0 text-success">R$ 37,90</h5>
                                <button class="btn btn-sm btn-outline-primary">Comprar</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-4">
                    <div class="card h-100">
                        <img src="https://images.unsplash.com/photo-1506880018603-83d5b814b5a6?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" class="card-img-top" alt="E-book">
                        <div class="card-body">
                            <h5 class="card-title">Redação para Concursos</h5>
                            <p class="card-text">Domine as técnicas para escrever textos nota 10 em qualquer prova discursiva.</p>
                            <div class="d-flex justify-content-between align-items-center">
                                <h5 class="mb-0 text-success">R$ 42,90</h5>
                                <button class="btn btn-sm btn-outline-primary">Comprar</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Spreadsheets -->
    <section id="planilhas" class="py-5 bg-light">
        <div class="container">
            <div class="text-center mb-5">
                <h2 class="section-title d-inline-block">Planilhas Inteligentes</h2>
                <p class="text-muted">Ferramentas para organizar seus estudos e maximizar seu desempenho</p>
            </div>
            
            <div class="row g-4">
                <div class="col-md-6">
                    <div class="card h-100">
                        <div class="card-body">
                            <div class="d-flex">
                                <div class="flex-shrink-0">
                                    <i class="fas fa-calendar-alt fa-3x text-primary me-4"></i>
                                </div>
                                <div>
                                    <h5 class="card-title">Planejador de Estudos</h5>
                                    <p class="card-text">Organize seu tempo de estudo por matérias, defina metas e acompanhe seu progresso.</p>
                                    <a href="#" class="btn btn-sm btn-outline-primary">Baixar Gratuitamente</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-6">
                    <div class="card h-100">
                        <div class="card-body">
                            <div class="d-flex">
                                <div class="flex-shrink-0">
                                    <i class="fas fa-chart-bar fa-3x text-success me-4"></i>
                                </div>
                                <div>
                                    <h5 class="card-title">Controle de Simulados</h5>
                                    <p class="card-text">Acompanhe seu desempenho em simulados e identifique seus pontos fortes e fracos.</p>
                                    <a href="#" class="btn btn-sm btn-outline-primary">Baixar Gratuitamente</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-6">
                    <div class="card h-100">
                        <div class="card-body">
                            <div class="d-flex">
                                <div class="flex-shrink-0">
                                    <i class="fas fa-wallet fa-3x text-info me-4"></i>
                                </div>
                                <div>
                                    <h5 class="card-title">Controle Financeiro</h5>
                                    <p class="card-text">Organize seus gastos com concursos e tenha total controle do seu orçamento.</p>
                                    <a href="#" class="btn btn-sm btn-outline-primary">Baixar Gratuitamente</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="col-md-6">
                    <div class="card h-100">
                        <div class="card-body">
                            <div class="d-flex">
                                <div class="flex-shrink-0">
                                    <i class="fas fa-book fa-3x text-warning me-4"></i>
                                </div>
                                <div>
                                    <h5 class="card-title">Revisão Espaçada</h5>
                                    <p class="card-text">Sistema de revisões baseado na curva do esquecimento para fixar o conteúdo.</p>
                                    <a href="#" class="btn btn-sm btn-outline-primary">Baixar Gratuitamente</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section id="depoimentos" class="py-5 bg-primary text-white">
        <div class="container">
            <div class="text-center mb-5">
                <h2 class="section-title d-inline-block text-white">Depoimentos</h2>
                <p class="opacity-75">O que nossos alunos dizem sobre a plataforma</p>
            </div>
            
            <div class="row g-4">
                <div class="col-md-4">
                    <div class="testimonial-card">
                        <div class="d-flex align-items-center mb-3">
                            <img src="https://randomuser.me/api/portraits/women/32.jpg" class="rounded-circle me-3" width="60" alt="Aluna">
                            <div>
                                <h5 class="mb-0">Ana Carolina</h5>
                                <p class="mb-0 text-primary">Aprovada no INSS</p>
                            </div>
                        </div>
                        <p class="mb-0">"O curso do Aprovado Digital foi fundamental para minha aprovação. O material é completo e os professores são excelentes!"</p>
                    </div>
                </div>
                
                <div class="col-md-4">
                    <div class="testimonial-card">
                        <div class="d-flex align-items-center mb-3">
                            <img src="https://randomuser.me/api/portraits/men/54.jpg" class="rounded-circle me-3" width="60" alt="Aluno">
                            <div>
                                <h5 class="mb-0">Ricardo Almeida</h5>
                                <p class="mb-0 text-primary">Aprovado na PRF</p>
                            </div>
                        </div>
                        <p class="mb-0">"As planilhas de organização de estudos transformaram minha rotina. Consegui otimizar meu tempo e focar no que realmente importava."</p>
                    </div>
                </div>
                
                <div class="col-md-4">
                    <div class="testimonial-card">
                        <div class="d-flex align-items-center mb-3">
                            <img src="https://randomuser.me/api/portraits/women/67.jpg" class="rounded-circle me-3" width="60" alt="Aluna">
                            <div>
                                <h5 class="mb-0">Juliana Santos</h5>
                                <p class="mb-0 text-primary">Aprovada na PF</p>
                            </div>
                        </div>
                        <p class="mb-0">"Os e-books são incríveis! Conteúdo direto ao ponto que me ajudou a reforçar os temas mais cobrados nas provas."</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Stats -->
    <section class="py-5 bg-white">
        <div class="container">
            <div class="row g-4">
                <div class="col-md-3">
                    <div class="stats-card stat-1">
                        <h3 class="display-4 fw-bold">2,500+</h3>
                        <p class="mb-0">Alunos Matriculados</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="stats-card stat-2">
                        <h3 class="display-4 fw-bold">97%</h3>
                        <p class="mb-0">Taxa de Satisfação</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="stats-card stat-3">
                        <h3 class="display-4 fw-bold">1,200+</h3>
                        <p class="mb-0">Aprovações</p>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="stats-card stat-4">
                        <h3 class="display-4 fw-bold">500+</h3>
                        <p class="mb-0">Materiais Disponíveis</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact -->
    <section id="contato" class="py-5 bg-light">
        <div class="container">
            <div class="text-center mb-5">
                <h2 class="section-title d-inline-block">Entre em Contato</h2>
                <p class="text-muted">Tire suas dúvidas ou solicite informações</p>
            </div>
            
            <div class="row g-4">
                <div class="col-lg-6">
                    <form>
                        <div class="mb-3">
                            <label class="form-label">Nome Completo</label>
                            <input type="text" class="form-control" required>
                        </div>
                        <div class="mb-3">
                            <label class="form-label">E-mail</label>
                            <input type="email" class="form-control" required>
                        </div>
                        <div class="mb-3">
                            <label class="form-label">Assunto</label>
                            <select class="form-select">
                                <option>Informações sobre cursos</option>
                                <option>Suporte técnico</option>
                                <option>Dúvidas sobre pagamento</option>
                                <option>Parcerias</option>
                            </select>
                        </div>
                        <div class="mb-3">
                            <label class="form-label">Mensagem</label>
                            <textarea class="form-control" rows="4" required></textarea>
                        </div>
                        <button type="submit" class="btn btn-primary">Enviar Mensagem</button>
                    </form>
                </div>
                
                <div class="col-lg-6">
                    <div class="card h-100">
                        <div class="card-body">
                            <h5 class="card-title mb-4">Informações de Contato</h5>
                            <ul class="list-unstyled">
                                <li class="mb-3">
                                    <div class="d-flex">
                                        <div class="flex-shrink-0">
                                            <i class="fas fa-map-marker-alt text-primary me-3"></i>
                                        </div>
                                        <div>
                                            <h6 class="mb-0">Endereço</h6>
                                            <p class="mb-0">Av. Brasil, 2000 - Rio de Janeiro, RJ</p>
                                        </div>
                                    </div>
                                </li>
                                <li class="mb-3">
                                    <div class="d-flex">
                                        <div class="flex-shrink-0">
                                            <i class="fas fa-phone-alt text-primary me-3"></i>
                                        </div>
                                        <div>
                                            <h6 class="mb-0">Telefone</h6>
                                            <p class="mb-0">(21) 99999-9999</p>
                                        </div>
                                    </div>
                                </li>
                                <li class="mb-3">
                                    <div class="d-flex">
                                        <div class="flex-shrink-0">
                                            <i class="fas fa-envelope text-primary me-3"></i>
                                        </div>
                                        <div>
                                            <h6 class="mb-0">E-mail</h6>
                                            <p class="mb-0">contato@aprovadodigital.com.br</p>
                                        </div>
                                    </div>
                                </li>
                                <li>
                                    <div class="d-flex">
                                        <div class="flex-shrink-0">
                                            <i class="fas fa-clock text-primary me-3"></i>
                                        </div>
                                        <div>
                                            <h6 class="mb-0">Horário de Atendimento</h6>
                                            <p class="mb-0">Segunda a Sexta: 9h às 18h</p>
                                        </div>
                                    </div>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="row g-4">
                <div class="col-lg-4">
                    <h5 class="mb-4">Aprovado Digital</h5>
                    <p>Sua plataforma completa para preparação em concursos públicos, com cursos, e-books e ferramentas inteligentes para sua aprovação.</p>
                    <div class="mt-4">
                        <a href="#" class="social-icon"><i class="fab fa-facebook-f"></i></a>
                        <a href="#" class="social-icon"><i class="fab fa-instagram"></i></a>
                        <a href="#" class="social-icon"><i class="fab fa-youtube"></i></a>
                        <a href="#" class="social-icon"><i class="fab fa-whatsapp"></i></a>
                    </div>
                </div>
                
                <div class="col-lg-2 col-md-4">
                    <h5 class="mb-4">Links Rápidos</h5>
                    <ul class="list-unstyled">
                        <li class="mb-2"><a href="#">Início</a></li>
                        <li class="mb-2"><a href="#cursos">Cursos</a></li>
                        <li class="mb-2"><a href="#ebooks">E-books</a></li>
                        <li class="mb-2"><a href="#planilhas">Planilhas</a></li>
                        <li><a href="#contato">Contato</a></li>
                    </ul>
                </div>
                
                <div class="col-lg-3 col-md-4">
                    <h5 class="mb-4">Cursos Populares</h5>
                    <ul class="list-unstyled">
                        <li class="mb-2"><a href="#">Preparatório INSS</a></li>
                        <li class="mb-2"><a href="#">Preparatório PRF</a></li>
                        <li class="mb-2"><a href="#">Preparatório PF</a></li>
                        <li class="mb-2"><a href="#">Preparatório Marinha</a></li>
                        <li><a href="#">Preparatório Tribunais</a></li>
                    </ul>
                </div>
                
                <div class="col-lg-3 col-md-4">
                    <h5 class="mb-4">Newsletter</h5>
                    <p>Inscreva-se para receber dicas de estudo e promoções exclusivas.</p>
                    <div class="input-group">
                        <input type="email" class="form-control" placeholder="Seu e-mail">
                        <button class="btn btn-primary">Inscrever</button>
                    </div>
                </div>
            </div>
            
            <hr class="mt-5 mb-4 border-secondary">
            
            <div class="text-center">
                <p class="mb-0">&copy; 2023 Aprovado Digital. Todos os direitos reservados.</p>
            </div>
        </div>
    </footer>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script>
        // Admin Panel Toggle
        document.getElementById('adminToggle').addEventListener('click', function() {
            const panel = document.getElementById('adminPanel');
            panel.style.display = panel.style.display === 'none' ? 'block' : 'none';
        });
        
        // Add Course Functionality
        document.getElementById('addCourseBtn').addEventListener('click', function() {
            const courseName = document.getElementById('courseName').value;
            const courseArea = document.getElementById('courseArea').value;
            const coursePrice = document.getElementById('coursePrice').value;
            const courseDescription = document.getElementById('courseDescription').value;
            
            if(courseName && courseArea && coursePrice) {
                alert(`Curso "${courseName}" adicionado com sucesso na área ${courseArea}!`);
                // Reset form
                document.getElementById('courseName').value = '';
                document.getElementById('coursePrice').value = '';
                document.getElementById('courseDescription').value = '';
            } else {
                alert('Por favor, preencha todos os campos obrigatórios.');
            }
        });
        
        // Add Student Functionality
        document.getElementById('addStudentBtn').addEventListener('click', function() {
            const studentName = document.getElementById('studentName').value;
            const studentEmail = document.getElementById('studentEmail').value;
            const studentCourse = document.getElementById('studentCourse').value;
            
            if(studentName && studentEmail && studentCourse) {
                alert(`Aluno ${studentName} matriculado com sucesso no ${studentCourse}!`);
                // Reset form
                document.getElementById('studentName').value = '';
                document.getElementById('studentEmail').value = '';
            } else {
                alert('Por favor, preencha todos os campos obrigatórios.');
            }
        });
        
        // Add E-book Functionality
        document.getElementById('addEbookBtn').addEventListener('click', function() {
            const ebookTitle = document.getElementById('ebookTitle').value;
            const ebookCategory = document.getElementById('ebookCategory').value;
            const ebookPrice = document.getElementById('ebookPrice').value;
            
            if(ebookTitle && ebookCategory && ebookPrice) {
                alert(`E-book "${ebookTitle}" adicionado com sucesso na categoria ${ebookCategory}!`);
                // Reset form
                document.getElementById('ebookTitle').value = '';
                document.getElementById('ebookPrice').value = '';
                document.getElementById('ebookFile').value = '';
            } else {
                alert('Por favor, preencha todos os campos obrigatórios.');
            }
        });
        
        // Add Sheet Functionality
        document.getElementById('addSheetBtn').addEventListener('click', function() {
            const sheetName = document.getElementById('sheetName').value;
            const sheetDescription = document.getElementById('sheetDescription').value;
            
            if(sheetName) {
                alert(`Planilha "${sheetName}" adicionada com sucesso!`);
                // Reset form
                document.getElementById('sheetName').value = '';
                document.getElementById('sheetDescription').value = '';
                document.getElementById('sheetFile').value = '';
            } else {
                alert('Por favor, informe o nome da planilha.');
            }
        });
    </script>
</body>
</html>
