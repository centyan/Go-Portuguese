# GO PORTUGUESE! — backend online

## Arquivos
- `main.py`: API FastAPI.
- `requirements.txt`: dependências Python.
- `render.yaml`: configuração de implantação no Render.
- `index.html`: página de demonstração para testar criar/entrar/iniciar salas.

## Publicar no Render
1. Envie estes arquivos para um repositório GitHub.
2. No Render, crie um **Blueprint** apontando para o repositório ou crie um **Web Service**.
3. Configure `TEACHER_PIN` como variável de ambiente secreta no Render. O `render.yaml` solicita esse valor (`sync: false`).
4. O serviço usa `gunicorn -w 1 -k uvicorn.workers.UvicornWorker main:app`.
5. Copie a URL pública do serviço e atualize `SERVER_URL` em `index.html`.

## Importante
- O `index.html` é uma demonstração mínima, não o jogo completo. Integre as chamadas de API ao `index.html` original do jogo.
- As salas ficam em memória; reinícios e implantações podem apagar as salas. O uso de um único worker evita que processos diferentes tenham cópias separadas da memória, mas não oferece persistência.
- O PIN antigo `adm@437` não é recomendado para produção. Configure um PIN forte por meio da variável `TEACHER_PIN`.
- CORS está aberto para facilitar testes. Em produção, restrinja `allow_origins` aos domínios do frontend.
- O polling apenas atualiza o status e placar; a página de demonstração não implementa a lógica completa do jogo.
