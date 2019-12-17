# documentations

#project react 

<h2>Criar Migration Sequelize-CLI</h2> <br/>
<p>yarn sequelize miigration:create --name=create-users <br/>
  <span> no arquivo criado, o <b>up</b> é a para definir os campos da tabela no banco.
    <span> no metodo <b> down </b> usado para drop da tabela.

# Execute migrations
Executar
<p>yarn sequelize db:migrate</p>
<h2>Desfazer a ultima </h2>
<p>yarn sequelize db:migrate:undo</p>
<h2>Desfazer todas as migrations </h2>
<p>yarn sequelize db:migrate:undo:all</p>

# Exemple model 
```
import Sequelize, { Model } from 'sequelize';
class User extends Model {
  static init(sequelize) {
    super.init(
      {
        name: Sequelize.STRING,
        email: Sequelize.STRING,
        password_hash: Sequelize.STRING,
        provider: Sequelize.STRING,
      },
      {
        sequelize,
      }
    );
  }
}

export default User;

```
