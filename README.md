# Controle-de-estacionamento
Projeto de desenvolvimento do sistema de controle de estacionamento com HTML, CSS e JavaScript. Ele inclui uma tela de cadastro de reservas e uma tela de listagem de vagas. O projeto não usa frameworks, como solicitado. Abaixo estão as etapas detalhadas para sua implementação.
1. Estrutura de pastas:
bash

/parking-system
    /css
        - styles.css
    /js
        - app.js
    /index.html
    /list.html
2. HTML e CSS:
1. Tela de cadastro (index.html)
html

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Vagas</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <h1>Cadastro de Reserva de Vaga</h1>
    <form id="reservationForm">
        <label for="plate">Placa do veículo:</label>
        <input type="text" id="plate" name="plate" required>

        <label for="owner">Nome do proprietário:</label>
        <input type="text" id="owner" name="owner" required>

        <label for="apartment">Número do apartamento:</label>
        <input type="number" id="apartment" name="apartment" required>

        <label for="block">Bloco do apartamento:</label>
        <input type="text" id="block" name="block" required>

        <label for="model">Modelo do veículo:</label>
        <input type="text" id="model" name="model" required>

        <label for="color">Cor do veículo:</label>
        <input type="text" id="color" name="color" required>

        <label for="slot">Número da vaga:</label>
        <input type="number" id="slot" name="slot" required>

        <button type="submit">Salvar</button>
    </form>

    <script src="js/app.js"></script>
</body>
</html>
2. Tela de listagem (list.html)
html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Vagas</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <h1>Vagas Cadastradas</h1>
    <table>
        <thead>
            <tr>
                <th>Placa</th>
                <th>Proprietário</th>
                <th>Apartamento</th>
                <th>Bloco</th>
                <th>Modelo</th>
                <th>Cor</th>
                <th>Vaga</th>
            </tr>
        </thead>
        <tbody id="parkingList">
            <!-- As vagas serão listadas aqui -->
        </tbody>
    </table>

    <script src="js/app.js"></script>
</body>
</html>
3. CSS (styles.css):
css

body {
    font-family: Arial, sans-serif;
    margin: 20px;
    padding: 20px;
    background-color: #f4f4f4;
}

h1 {
    text-align: center;
}

form, table {
    width: 80%;
    margin: 0 auto;
}

label {
    display: block;
    margin: 10px 0 5px;
}

input {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    width: 100%;
    padding: 10px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

table {
    width: 100%;
    margin-top: 20px;
    border-collapse: collapse;
}

th, td {
    padding: 12px;
    text-align: left;
    border-bottom: 1px solid #ddd;
}
4. JavaScript (app.js):
javascript

// Array para armazenar as vagas
let parkingSlots = [];

// Ação do botão "Salvar" na página de cadastro
document.getElementById("reservationForm")?.addEventListener("submit", function (event) {
    event.preventDefault();

    // Obter valores do formulário
    const plate = document.getElementById("plate").value;
    const owner = document.getElementById("owner").value;
    const apartment = document.getElementById("apartment").value;
    const block = document.getElementById("block").value;
    const model = document.getElementById("model").value;
    const color = document.getElementById("color").value;
    const slot = document.getElementById("slot").value;

    // Criar objeto com os dados da vaga
    const parkingSlot = {
        plate,
        owner,
        apartment,
        block,
        model,
        color,
        slot
    };

    // Adicionar vaga ao array
    parkingSlots.push(parkingSlot);

    // Exibir no console
    console.log(parkingSlots);

    // Pop-up de sucesso
    alert("Cadastro realizado com sucesso!");

    // Limpar o formulário
    this.reset();
});

// Exibir as vagas na tela de listagem
window.onload = function () {
    const parkingList = document.getElementById("parkingList");
    if (parkingList) {
        parkingSlots.forEach((slot) => {
            const row = `<tr>
                <td>${slot.plate}</td>
                <td>${slot.owner}</td>
                <td>${slot.apartment}</td>
                <td>${slot.block}</td>
                <td>${slot.model}</td>
                <td>${slot.color}</td>
                <td>${slot.slot}</td>
            </tr>`;
            parkingList.innerHTML += row;
        });
    }
};
Explicação do código:
1.	index.html (Tela de Cadastro): Esta página contém um formulário para o usuário inserir os dados do veículo, do proprietário e a vaga. Ao submeter o formulário, os dados são armazenados em um array parkingSlots no JavaScript, exibidos no console.log e o formulário é limpo após o envio bem-sucedido.
2.	list.html (Tela de Listagem): Esta página exibe as vagas armazenadas. O JavaScript gera linhas de tabela para cada vaga registrada, exibindo as informações do veículo e da vaga.
3.	styles.css: O arquivo CSS estiliza o formulário e a tabela para torná-los mais agradáveis visualmente.
4.	app.js: Este arquivo JavaScript gerencia o armazenamento dos dados e a exibição deles nas duas telas. A função de envio de formulário armazena os dados e, quando a tela de listagem é carregada, a função window.onload preenche a tabela com os dados das vagas.
Como testar o sistema:
1.	Abra a página index.html em seu navegador e preencha o formulário com as informações solicitadas.
2.	Ao clicar no botão "Salvar", as informações aparecerão no console (pressione F12 para abrir o console no navegador).
3.	Em seguida, abra a página list.html, onde será possível visualizar a tabela de vagas cadastradas.
Considerações:
•	O projeto foi construído sem o uso de frameworks.
•	Não há persistência de dados, pois não há back-end ou banco de dados.
•	É possível expandir o projeto posteriormente com um back-end para armazenamento real de dados.
