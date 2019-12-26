# Récupérer des données stockées avec Doctrine.
### Envoyer des requetes via le shell avec doctrine.
```shell
php bin/console doctrine:query:sql 'INSERT INTO category VALUES (1, "Horreur");'

php bin/console doctrine:query:sql 'INSERT INTO program (id, title, summary, poster, category_id) VALUES (NULL, "Walking Dead", "Le policier Rick Grimes se réveille après un long coma. Il découvre avec effarement que le monde, ravagé par une épidémie, est envahi par les morts-vivants.", "https://m.media-amazon.com/images/M/MV5BZmFlMTA0MmUtNWVmOC00ZmE1LWFmMDYtZTJhYjJhNGVjYTU5XkEyXkFqcGdeQXVyMTAzMDM4MjM0._V1_.jpg", 1);'

php bin/console doctrine:query:sql 'INSERT INTO program (id, title, summary, poster, category_id) VALUES (NULL, "The Haunting Of Hill House", "Plusieurs frères et sœurs qui, enfants, ont grandi dans la demeure qui allait devenir la maison hantée la plus célèbre des États-Unis, sont contraints de se réunir pour finalement affronter les fantômes de leur passé.", "https://m.media-amazon.com/images/M/MV5BMTU4NzA4MDEwNF5BMl5BanBnXkFtZTgwMTQxODYzNjM@._V1_SY1000_CR0,0,674,1000_AL_.jpg", 1);'

php bin/console doctrine:query:sql 'INSERT INTO program (id, title, summary, poster, category_id) VALUES (NULL, "American Horror Story", "A chaque saison, son histoire. American Horror Story nous embarque dans des récits à la fois poignants et cauchemardesques, mêlant la peur, le gore et le politiquement correct.", "https://m.media-amazon.com/images/M/MV5BODZlYzc2ODYtYmQyZS00ZTM4LTk4ZDQtMTMyZDdhMDgzZTU0XkEyXkFqcGdeQXVyMzQ2MDI5NjU@._V1_SY1000_CR0,0,666,1000_AL_.jpg", 1);'

php bin/console doctrine:query:sql 'INSERT INTO program (id, title, summary, poster, category_id) VALUES (NULL, "Love Death And Robots", "Un yaourt susceptible, des soldats lycanthropes, des robots déchaînés, des monstres-poubelles, des chasseurs de primes cyborgs, des araignées extraterrestres et des démons assoiffés de sang : tout ce beau monde est réuni dans 18 courts métrages animés déconseillés aux âmes sensibles.", "https://m.media-amazon.com/images/M/MV5BMTc1MjIyNDI3Nl5BMl5BanBnXkFtZTgwMjQ1OTI0NzM@._V1_SY1000_CR0,0,674,1000_AL_.jpg", 1);'

php bin/console doctrine:query:sql 'INSERT INTO program (id, title, summary, poster, category_id) VALUES (NULL, "Penny Dreadful", "Dans le Londres ancien, Vanessa Ives, une jeune femme puissante aux pouvoirs hypnotiques, allie ses forces à celles de Ethan, un garçon rebelle et violent aux allures de cowboy, et de Sir Malcolm, un vieil homme riche aux ressources inépuisables. Ensemble, ils combattent un ennemi inconnu, presque invisible, qui ne semble pas humain et qui massacre la population.", "https://m.media-amazon.com/images/M/MV5BNmE5MDE0ZmMtY2I5Mi00Y2RjLWJlYjMtODkxODQ5OWY1ODdkXkEyXkFqcGdeQXVyNjU2NjA5NjM@._V1_SY1000_CR0,0,695,1000_AL_.jpg", 1);'

php bin/console doctrine:query:sql 'INSERT INTO program (id, title, summary, poster, category_id) VALUES (NULL, "Fear The Walking Dead", "La série se déroule au tout début de l épidémie relatée dans la série mère The Walking Dead et se passe dans la ville de Los Angeles, et non à Atlanta. Madison est conseillère dans un lycée de Los Angeles. Depuis la mort de son mari, elle élève seule ses deux enfants : Alicia, excellente élève qui découvre les premiers émois amoureux, et son grand frère Nick qui a quitté la fac et a sombré dans la drogue.", "https://m.media-amazon.com/images/M/MV5BYWNmY2Y1NTgtYTExMS00NGUxLWIxYWQtMjU4MjNkZjZlZjQ3XkEyXkFqcGdeQXVyMzQ2MDI5NjU@._V1_SY1000_CR0,0,666,1000_AL_.jpg", 1);'
```
### FindAll()
```php
/**
 * Show all rows from Program’s entity
 *
 * @Route("/", name="wild_index")
 * @return Response A response instance
 */
 public function index(): Response
 {
      $programs = $this->getDoctrine()
          ->getRepository(Program::class)
          ->findAll();

      if (!$programs) {
          throw $this->createNotFoundException(
          'No program found in program\'s table.'
          );
      }

      return $this->render(
              'wild/index.html.twig',
              ['programs' => $programs]
      );
}
```
### La vue templates/wild/index.html.twig
```php
{% extends 'base.html.twig' %}

{% block title %}All programs{% endblock %}

{% block body %}
    <h1>Toutes les séries de la table program : </h1>
    {% for program in programs %}
        <div>
            <h2>{{ loop.index }} / {{ program.title }} - Catégorie : {{ program.category.name }}</h2>
            <p>{{ program.summary }}</p>
        </div>
    {% else %}
        Aucune série trouvée.
    {% endfor %}
    <a href="{{ path('app_index') }}">
        Retour à l'accueil
    </a>
{% endblock %}
```
### findOneBy()
```php
/**
    * Getting a program with a formatted slug for title
    *
    * @param string $slug The slugger
    * @Route("/show/{slug<^[a-z0-9-]+$>}", defaults={"slug" = null}, name="show")
    * @return Response
    */
    public function show(?string $slug):Response
    {
        if (!$slug) {
            throw $this
                ->createNotFoundException('No slug has been sent to find a program in program\'s table.');
        }
        $slug = preg_replace(
            '/-/',
            ' ', ucwords(trim(strip_tags($slug)), "-")
        );
        $program = $this->getDoctrine()
            ->getRepository(Program::class)
            ->findOneBy(['title' => mb_strtolower($slug)]);
        if (!$program) {
            throw $this->createNotFoundException(
                'No program with '.$slug.' title, found in program\'s table.'
            );
        }

        return $this->render('wild/show.html.twig', [
            'program' => $program,
            'slug'  => $slug,
        ]);
    }
    
 ```
 ### Il ne te reste plus qu'à adapter ta vue au retour de ta méthode show(string $slug) :
 ```php
    
    {# templates/wild/show.html.twig #}
{% extends 'base.html.twig' %}
{% block title %}{{ slug }}{% endblock %}

{% block body %}

<div class="media">
  <img class="align-self-start mr-3" src="{{program.poster}}" alt="{{ program.title }} poster">
  <div class="media-body">
    <h1 class="mt-0">{{ program.title }}</h1>
    <p>{{ program.summary }}</p>
    <p>Categorie : {{ program.category.name }}</p>
  </div>
</div>

<a href="{{ path('wild_index') }}">
    Retour à l'accueil
</a>

{% endblock %}

```
  