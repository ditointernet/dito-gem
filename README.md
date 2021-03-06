# Dito

Essa gem tem como objetivo automatizar a integração com a Rest API da Dito.

## Instalação

Adicione a linha abaixo no arquivo ``Gemfile`` da sua aplicação:

    gem 'dito'

Execute:

    $ bundle

Ou instale manualmente:

    $ gem install dito

## Uso

### Configurando sua aplicação

Adicione o código abaixo em cada ambiente de configuração da sua aplicação.

    Dito.configure do |c|
      c.api_key = 'SUA_API_KEY'
      c.secret = 'SUA_SECRET'
    end

As chaves da sua aplicação podem ser encontradas na área de configuração do seu aplicativo na plataforma da Dito.

### Enviando seus usuários

O método ``Dito.identify`` é usado para enviar os usuários da sua aplicação para a plataforma da Dito.

O nó data é reservado para as informações do usuários relativas a sua aplicação. Fique a vontade para enviar quantas informações quiser.

Exemplo:
  
    Dito.identify({
      id: Digest::SHA1.hexdigest('marcos.nogueira@dito.com.br'),
      name: 'Marcos Nogueira',
      email: 'marcos.nogueira@dito.com.br'
    })

    # Ou

    Dito.identify({
      facebook_id: '123141312312',
      access_token: 'XXXXXXXXXX',
      data: {
        cpf: '101.032.076-95',
        cargo: 'Desenvolvedor'
      }
    })

### Criando eventos

O método ``Dito.track`` é usado para trackear o comportamento dos usuários na forma de eventos em sua aplicação.

O nó data é reservado para as informações do evento. Fique a vontade para enviar quantas informações quiser.

Exemplo:

    Dito.track({
      id: Digest::SHA1.hexdigest('marcos.nogueira@dito.com.br'),
      event: {
        action: 'nome-do-evento',
        revenue: 5.99, // Opcional
        data: {
          propriedade_1: 'valor da propriedade 1',
          propriedade_2: 'valor da propriedade 2'
        }
      }
    })

## Contributing

1. Fork it ( http://github.com/<my-github-username>/dito/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
