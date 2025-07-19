## 🌍 Configurando Domínio para Servidor de Minecraft

Um dos grandes diferenciais de um servidor de Minecraft profissional é possuir um domínio amigável, como `play.seuservidor.com`, em vez de algo como `mc.seuservidor.com:25565`.  
Aqui está um **guia completo** para configurar seu domínio, com ou sem **SRV**, utilizando **Cloudflare** e **Hostinger**.

---

### **1. O Que é o Registro SRV?**
- O registro **SRV** (Service Record) é utilizado para apontar o **host e a porta** de um serviço.
- Com SRV, você pode **ocultar a porta do servidor**, permitindo que os jogadores conectem-se apenas digitando `play.seuservidor.com`.

---

## **2. Configurando na Cloudflare**

### **2.1 Sem SRV (usando apenas A ou CNAME):**
- **Passo 1:** Acesse seu painel da **Cloudflare**.
- **Passo 2:** Vá em **DNS > Gerenciar registros**.
- **Passo 3:** Crie um registro `A`:
  - **Nome:** `play` (ficará `play.seuservidor.com`).
  - **IPv4:** IP do servidor Minecraft.
  - **TTL:** Auto ou 300.
  - **Proxy:** **Desativado** (Cloudflare proxy não funciona com Minecraft).
- **Passo 4:** Para conectar, use `play.seuservidor.com:porta`.

---

### **2.2 Com SRV (sem mostrar a porta):**
- **Passo 1:** Ainda na aba DNS, crie um registro `A` apontando para o IP (igual ao passo anterior).
- **Passo 2:** Agora crie um registro `SRV`:
  - **Tipo:** `SRV`.
  - **Serviço:** `_minecraft`.
  - **Protocolo:** `_tcp`.
  - **Nome:** `play`.
  - **Destino:** `play.seuservidor.com`.
  - **Porta:** `25565` (ou a porta que você configurou).
  - **Peso & Prioridade:** 0.
  - **TTL:** Auto.

---

## **3. Configurando na Hostinger**

O processo na Hostinger é bem semelhante ao da Cloudflare:

### **3.1 Sem SRV:**
- **Passo 1:** Vá em **Gerenciar Domínio > Zona DNS**.
- **Passo 2:** Crie um registro `A`:
  - **Nome:** `play`.
  - **IP:** IP do servidor Minecraft.
  - **TTL:** 300 ou Auto.

---

### **3.2 Com SRV:**
- **Passo 1:** Crie o registro `A` da mesma forma.
- **Passo 2:** Adicione o registro `SRV`:
  - **Serviço:** `_minecraft`.
  - **Protocolo:** `_tcp`.
  - **Prioridade:** `0`.
  - **Peso:** `5`.
  - **Porta:** `25565`.
  - **Destino:** `play.seuservidor.com`.

---

## **4. Testando o Domínio**
- Após configurar, aguarde a **propagação DNS** (normalmente até 15 minutos).
- Teste no Minecraft usando apenas `play.seuservidor.com`.
- Se estiver usando sem SRV, será necessário informar a porta: `play.seuservidor.com:25565`.

---

## 🎯 **Dica de Segurança**
- Utilize **Cloudflare** para proteger o domínio e ocultar o IP real do servidor (para ataques DDoS).
- Para isso, é necessário usar um **proxy de TCP/UDP** (com Cloudflare Spectrum ou serviços como TCPShield).

---

## 📫 **Onde me encontrar**
- **GitHub:** [campoyerick](https://github.com/campoyerick)
- **Email:** campoyrick@gmail.com
- **Discord:** `erickcampoyp`

---

<p align="center">
  Feito com ❤️ por <a href="https://github.com/campoyerick">Erick</a>
</p>
