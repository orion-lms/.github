Orion LMS 🌗🤖

LMS platform integrate with sophisticated ai assistant.

## 🗂️ **Plano de Desenvolvimento**

### **FASE 1: FUNDAÇÃO E CONFIGURAÇÃO** ✅

- [x] **Setup do Projeto**
  - [x] Criar estrutura de pastas (`src/`, `infrastructure/`, `scripts/`)
  - [x] Configurar TypeScript + Effect TS
  - [x] Configurar ESLint + Prettier
  - [x] Criar scripts básicos (dev, build, start, example)
  - [x] Configurar dependências corretas do Effect TS

- [x] **Configuração Local**
  - [x] Instalar FFmpeg localmente
  - [x] Configurar variáveis de ambiente
  - [x] Criar Dockerfile básico
  - [x] Testar build do container

- [x] **Aprendizado Effect TS**
  - [x] Estudar conceitos básicos (Effect, Either, Option)
  - [x] Implementar primeiros exemplos
  - [x] Entender error handling funcional
  - [x] Testar com exemplo funcional

- [x] **Simplificação da Arquitetura**
  - [x] Remover Tags, Providers, Layers e DI avançada
  - [x] Implementar factory functions simples
  - [x] Garantir uso direto dos serviços
  - [x] Documentar abordagem simplificada

### **FASE 2: CORE DO ENCODER** ✅

- [x] **Estrutura Base**
  - [x] Criar tipos TypeScript para jobs
  - [x] Implementar configurações FFmpeg (estrutura)
  - [x] Criar sistema de logging com Effect

- [x] **Processamento de Vídeo**
  - [x] Implementar encoding básico com FFmpeg
  - [x] Criar sistema de resoluções múltiplas
  - [x] Implementar processamento concorrente
  - [x] Adicionar progress tracking

- [x] **File Watching**
  - [x] Implementar Chokidar para monitorar arquivos
  - [x] Criar sistema de upload em tempo real
  - [x] Implementar isolamento por resolução

- [x] **SQS Worker**
  - [x] Implementar polling de mensagens
  - [x] Criar parser de jobs
  - [x] Implementar processamento de fila

- [x] **SNS Notifications**
  - [x] Implementar envio de notificações
  - [x] Criar progress tracking
  - [x] Adicionar error handling

### **FASE 3: INTEGRAÇÃO COM STORAGE** ✅

- [x] **Cloudflare R2**
  - [x] Configurar credenciais R2
  - [x] Implementar upload de arquivos
  - [x] Criar sistema de retry
  - [x] Adicionar progress tracking de upload

- [x] **HLS Generation**
  - [x] Implementar geração de playlists HLS
  - [x] Criar master playlist
  - [x] Gerar thumbnails automáticos
  - [x] Implementar cleanup de arquivos temporários

- [x] **Pipeline Completo**
  - [x] Implementar processamento paralelo de resoluções
  - [x] Criar real-time upload com watchers
  - [x] Implementar coordenação entre serviços
  - [x] Adicionar progress tracking completo

### **FASE 4: INFRAESTRUTURA AWS** ☁️

- [ ] **Setup AWS**
  - [ ] Configurar AWS CLI
  - [ ] Criar usuário IAM com permissões
  - [ ] Configurar Pulumi
  - [ ] Criar primeiro recurso (SQS)

- [ ] **Recursos Básicos**
  - [ ] Criar SQS queue
  - [ ] Configurar SNS topic
  - [ ] Criar ECR repository
  - [ ] Configurar Auto Scaling Group

- [ ] **EC2 Configuration**
  - [ ] Criar Launch Template
  - [ ] Configurar Spot Instances
  - [ ] Configurar Security Groups
  - [ ] Implementar user data script

### **FASE 5: AUTO-SCALING** ⚡

- [ ] **Lambda Function**
  - [ ] Implementar Lambda de scaling
  - [ ] Configurar CloudWatch Events
  - [ ] Testar trigger automático
  - [ ] Implementar lógica de escala

- [ ] **Integração Completa**
  - [ ] Conectar SQS → Lambda → EC2
  - [ ] Testar ciclo completo
  - [ ] Implementar health checks
  - [ ] Adicionar métricas

### **FASE 6: OTIMIZAÇÃO E MONITORAMENTO** 📊

- [ ] **Performance**
  - [ ] Otimizar configurações FFmpeg
  - [ ] Implementar cost tracking
  - [ ] Adicionar retry logic
  - [ ] Otimizar uso de memória

- [ ] **Observabilidade**
  - [ ] Implementar tracing com Effect
  - [ ] Configurar CloudWatch logs
  - [ ] Adicionar métricas customizadas
  - [ ] Criar dashboards

### **FASE 7: TESTES E DEPLOY** 🚀

- [ ] **Testes**
  - [ ] Testes locais completos
  - [ ] Testes em nuvem
  - [ ] Testes de carga
  - [ ] Validação de custos

- [ ] **Documentação**
  - [x] Atualizar README
  - [ ] Documentar configurações
  - [ ] Criar guia de troubleshooting
  - [ ] Documentar presets de encoding

## 🎯 **ESTRATÉGIA DE CUSTOS**

### **Spot Instances**

- **c8g.16xlarge**: ~$0.70/hora (spot) vs $2.50/hora (on-demand)
- **Economia**: ~72% de desconto

### **Auto-scaling**

- **Mínimo**: 0 instâncias (quando não há jobs)
- **Máximo**: 5 instâncias (configurável)
- **Trigger**: 1 job = 1 worker

## 🛠️ **TECNOLOGIAS E FERRAMENTAS**

### **Core:**

- **Node.js 22+** com TypeScript
- **Effect TS** para modelar efeitos, concorrência e error handling funcional
- **FFmpeg** para encoding de vídeo
- **Chokidar** para file watching

### **Arquitetura:**

- **Factory Functions** para criar serviços (sem DI avançada)
- **Uso direto** de serviços (sem Tags, Providers, Layers)
- **Simplicidade** como prioridade

### **Cloud (AWS):**

- **EC2 Spot Instances** (c8g.16xlarge - 64 vCPU, 128GB RAM)
- **SQS** para fila de jobs
- **SNS** para notificações
- **Auto Scaling Group** para escalabilidade
- **ECR** para container registry
- **Lambda** para auto-scaling

### **Storage:**

- **Cloudflare R2** ou **AWS S3** para arquivos
- **EBS** (30GB) para storage temporário
