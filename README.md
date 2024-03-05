Este projeto implementa um sistema simplificado inspirado no PicPay, onde dois tipos de usuários (comuns e lojistas) podem realizar transferências entre si. O sistema é desenvolvido em Java e inclui funcionalidades como cadastro de usuários, validações, transferências, consulta a serviço autorizador externo e notificações de pagamento.

## Funcionalidades Principais

1. **Cadastro de Usuários:**
   - Cadastro de usuários comuns e lojistas com Nome Completo, CPF, e-mail e Senha.
   - Garante unicidade de CPF/CNPJ e e-mails no sistema.
   - Endpoint: `POST /users`
     ```json
     {
         "firstName": "Pedro",
         "lastName": "Alves",
         "document": "12332122",
         "email": "teste1@gmail.com",
         "password": "senha",
         "balance": 100,
         "userType": "COMMON"
     }
     ```
     Para criar um lojista, utilize `"userType": "MERCHANT"`.

2. **Transferência de Dinheiro:**
   - Usuários podem enviar dinheiro entre si ou para lojistas.
   - Lojistas apenas recebem transferências.
   - Endpoint: `POST /transactions`
     ```json
     {
         "value": 10,
         "senderId": 1,
         "receiverId": 5
     }
     ```

3. **Validação de Saldo:**
   - Verifica se o usuário possui saldo suficiente antes de realizar uma transferência.

4. **Consulta a Serviço Autorizador Externo:**
   - Antes de concluir a transferência, o sistema consulta um serviço autorizador externo (mock fornecido).

5. **Transação Atômica:**
   - A transferência é tratada como uma transação, revertendo-se em caso de inconsistência. O dinheiro volta para a carteira do remetente.

6. **Notificações de Pagamento:**
   - Notifica usuários ou lojistas sobre recebimento de pagamento através de um serviço de terceiros (mock fornecido).
   - Lida com possíveis indisponibilidades ou instabilidades do serviço de notificação.

7. **Endpoint RESTFul:**
   - Implementação de um serviço RESTFul com endpoint `POST /transactions`.
   - Payload exemplo:
     ```json
     {
         "value": 10,
         "senderId": 1,
         "receiverId": 5
     }
     ```

## Como Utilizar

1. Clone o repositório.
2. Configure o ambiente Java.
3. Execute a aplicação.
4. Utilize os endpoints `POST /users` e `POST /transactions` para criar usuários e realizar transferências, respectivamente.
