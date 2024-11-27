# POC-6
## Sistemas de Informação, 02J L12
### Andreas Caycedo Martinez, 10435302
### Caio Takehiro Magnoli Igari, 10437809

Esta última POC demonstra como criar uma interface para reserva de assentos em cinemas utilizando React e Next.js. O projeto explora conceitos como manipulação de estado, responsividade e alternância de temas. Abaixo, você encontrará os principais destaques da aplicação que realizamos.

---

## Estrutura do Projeto

Esta POC foca no uso de um design modular com React, destacando-se pelos seguintes pontos:

- **Manipulação de Estado**: Uso do `useState` e `useEffect` para gerenciar o tema e a seleção de assentos.
- **Componentização**: Organização de componentes reutilizáveis, como `SeatGrid`, `MovieDetails` e `Legend`.
- **CSS Temático**: Aplicação de variáveis de CSS para suportar temas claro e escuro de forma eficiente.
- **Design Responsivo**: Estilização adaptada para dispositivos móveis e desktops.

A estrutura modular facilita a manutenção e evolução do código.

---

## Componentes Simples e Interativos

### Exemplo: Alternância de Tema

O botão para alternar entre os temas claro e escuro demonstra como um componente interativo pode alterar dinamicamente o estilo da aplicação. 

```jsx
const toggleTheme = () => setTheme(theme === 'light' ? 'dark' : 'light');

<button className="theme-toggle" onClick={toggleTheme}>
  {theme === 'light' ? 'Escuro' : 'Claro'}
</button>;
```

### Exemplo: Seleção de Assentos

A lógica de seleção é implementada no componente principal, onde o estado de cada assento é gerenciado:

```jsx
const toggleSeat = (seatId) => {
  if (movieData.assentos[seatId]?.invisivel) return;

  setSelectedSeats((prev) =>
    prev.includes(seatId) ? prev.filter((id) => id !== seatId) : [...prev, seatId]
  );
};
```

## Estilo CSS (Temático e Responsivo)

### Tema Claro e Escuro 

Os estilos são definidos com variáveis CSS no seletor ":root" e aplicados dinamicamente com o atributo "data-theme". Exemplo de configuração de tema:

```css
:root {
  --primary: #DB3D2E;
  --background: #F0F0F0;
  --text: #1A1A24;
}

[data-theme='dark'] {
  --background: #1A1A24;
  --text: #F0F0F0;
}
```

### Estilos Responsivos

O design responsivo é implementado com media queries para garantir uma boa experiência em telas menores:

```css
@media (max-width: 768px) {
  .content-wrapper {
    flex-direction: column;
  }

  .seat {
    width: 30px !important;
    height: 30px !important;
  }
}
```

## Componentização

### Grid de Assentos (SeatGrid.js)

Renderiza o layout de assentos, utilizando um grid CSS para organizar os assentos disponíveis, ocupados e invisíveis:

```jsx
<div className="seat-grid">
  {seats.map((seat) => (
    <div
      key={seat.numero}
      className={`seat ${seat.disponivel ? '' : 'occupied'} ${seat.invisivel ? 'invisivel' : ''}`}
      onClick={() => toggleSeat(seat.numero - 1)}
    ></div>
  ))}
</div>
```

### Detalhes do Filme (MovieDetails.js)

Exibe informações do filme em exibição:

```jsx
export default function MovieDetails({ movie }) {
  return (
    <div className="movie-details">
      <div className="label">Sinopse:</div>
      <p>{movie.sinopse}</p>
      <div className="label">Data de Lançamento:</div>
      <p>{movie.dataLancamento}</p>
      <div className="label">Direção:</div>
      <p>{movie.direcao}</p>
    </div>
  );
}
```

## Como Rodar o Projeto

Para acessar o resultado, siga os passos abaixo:

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/cinema-booking.git
cd cinema-booking
```

2. Instale as dependências:

```bash
npm install
```

3. Inicie o servidor local:

```bash
npm start
```

4. Abra o navegador e acesse:

```bash
[npm install](http://localhost:3000)
```

## Resultado Visual

O resultado do código pode ser visualizado no layout abaixo:

![image](https://github.com/user-attachments/assets/57a6e704-7bfb-45fb-8a4e-bec0d71a98a3)

![image](https://github.com/user-attachments/assets/9dfe54fc-0c29-4e58-9776-9a5b6023c20f)

![image](https://github.com/user-attachments/assets/46cda1c0-b87c-4c10-bb4a-673e5682ebd7)

![image](https://github.com/user-attachments/assets/571ad3cf-382f-4fb4-b6fd-3d5b21be2904)


## Conclusão

Em suma, essa POC contém:

- Alternância de tema claro/escuro.
- Gerenciamento eficiente de estados para seleção de assentos.
- Design responsivo para suportar múltiplas plataformas.

E foi isso o que desenvolvemos!
