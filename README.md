# Crypto + Jewelry Starter (Full-Stack)

Starter empaquetado que cumple los requisitos solicitados: landing, autenticación con JWT y 2FA (TOTP),
cartera cripto (lectura y envío simulado), catálogo de joyería con filtros y carrito, módulo de administración
(usuarios, inventario, pedidos), i18n ES/EN, roles y permisos, y estructura preparada para SSL/HTTPS, Docker y despliegue.

> **Nota:** Este es un **starter** funcional con endpoints y vistas base, pensado para desplegar rápido
y extender. Incluye mocks y puntos de integración (blockchain, pagos, KYC, transportadoras).

## Estructura
```
/backend        # API Node.js (Express) + JWT + 2FA (TOTP) + Mongoose
/frontend       # React + Vite + Tailwind + React Router + i18n
/docs           # Documentación y mapa de requisitos
docker-compose.yml
.env.example
```

## Requisitos previos
- Node.js 18+ y npm
- Docker (opcional, recomendado)
- MongoDB (o usar el servicio de docker-compose)

## Variables de entorno
Copia `.env.example` a `.env` y ajusta valores.

## Ejecutar con Docker (recomendado)
```bash
docker compose up --build
```
- UI: http://localhost:5173
- API: http://localhost:4000/api

## Ejecutar local (sin Docker)
```bash
# Backend
cd backend
npm i
npm run dev

# Frontend (en otra terminal)
cd frontend
npm i
npm run dev
```
- UI: http://localhost:5173
- API: http://localhost:4000/api

## Integraciones
- **Blockchain**: `ethers` (leer balances, preparar transacciones) – archivo `frontend/src/lib/blockchain.js`.
- **2FA TOTP**: `speakeasy` + `qrcode` en backend para generar secretos y QR.
- **JWT**: login/registro y middleware con roles.
- **KYC**: endpoint y stub para integración externa.
- **Pagos**: stubs para tarjeta/PayPal/cripto.
- **Transportadoras**: stubs DHL/FedEx/Deprisa.
- **SEO**: metatags básicos y sitemap stub.
- **Modo oscuro/claro**: alternador en la UI.
- **i18n**: ES/EN con archivos JSON.

## Aviso de seguridad
- SSL/HTTPS debe configurarse en el reverso (Nginx/traefik) o PaaS.
- Nunca almacenes claves privadas en texto plano. Usa HW wallets o custodia externa.
- Revisa y endurece CORS, rate limiting, y validaciones antes de producción.
