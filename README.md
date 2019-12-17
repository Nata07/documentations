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

# Exemple Controller 
```
import User from '../models/User';

class UserController {
  async store(req, res) {
    const userExist = await User.findOne({ where: { email: req.body.email } });

    if (userExist) {
      return res.status(400).json({ message: 'User already exists.' });
    }
    const { id, name, email, provider } = await User.create(req.body);

    return res.json({
      id,
      name,
      email,
      provider,
    });
  }
}

export default new UserController();

```

