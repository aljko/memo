## Routage
### Pour lister toutes les route d'une projet Symfony
```shell
bin/console debug:router
```
### Définir de parametrage de route annotations
```php
class WildController extends AbstractController
{
    /**
     * @Route("/wild/show/{slug}",
     *     name="wild_show",
     *     requirements={"slug"="^[a-z0-9-]+$"}
     *     ))
     */
    public function show(string $slug): Response
    {
        return $this->render('wild/show.html.twig', ['slug' => $slug]);
    }

    /**
     * @Route("/wild", name="wild_index")
     */
    public function index() :Response
    {
        return $this->render('wild/index.html.twig', [
            'website' => 'Wild Séries',
        ]);
    }