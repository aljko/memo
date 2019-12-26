# Création d'une page.

### Un contrôleur en Symfony doit étendre
    Symfony\Bundle\Framework\Bundle\Controller\AbstractController
    
### L'objet Response

```php
<?php
        // src/Controller/WildController.php
        namespace App\Controller;

        use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
        use Symfony\Component\HttpFoundation\Response;

        class WildController extends AbstractController
        {
            public function index() :Response
            {
                return new Response(
                    '<html><body>Wild Series Index</body></html>'
                );
            }
        }
```

### Route en YAML

```yaml
# config/routes.yaml

# the "wild_index" route name is not important yet
wild_show_index:
    path: /wild/
    controller: App\Controller\WildController::index
```

### Route en annotations

```shell
composer require annotations
```

```php
[...]
use Symfony\Component\Routing\Annotation\Route;

Class WildController extends AbstractController
{
    /**
     * @Route("/wild", name="wild_index")
    */
    public function index() : Response
    {
        return new Response(
            '<html><body>Wild Series Index</body></html>'
        );
    }
}
```
### Appeler un *template* Twig

```php
/**
     * @Route("/wild", name="wild_index")
    */
public function index() :Response
{
    return $this->render('wild/index.html.twig', [
            'website' => 'Wild Séries',
    ]);
}
```




