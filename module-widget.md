
# Module Widget

`Widget` facade is very helpful for adding an widget for your custom module. Let say you want add a simple widget for your featured product custom module for AvoRed E commerce. You can do that simply adding into your `module.php` files `boot` method by registering a Widget.

    use AvoRed\Framework\Widget\Facade as WidgetFacade;
    use AvoRed\Featured\Widget\Featured\Widget;
    
    
    $featuredProduct = new Widget();
    WidgetFacade::make($featuredProduct->identifier(), $featuredProduct);


#### How to create a Widget Class

Only one main thing to keep in mind when creating a Widget class is to use `WidgetContract` for your widget class. Let say we want to implement an Widget Class for a Feature Product. It can be done using an simple way as shown below:

    <?php

    namespace AvoRed\Featured\Widget\Featured;

    use AvoRed\Framework\Models\Database\ProductPropertyIntegerValue;
    use AvoRed\Framework\Repository\Product;
    use AvoRed\Framework\Widget\Contracts\Widget as WidgetContract;
    use Illuminate\Support\Collection;

    class Widget implements WidgetContract
    {



        /**
         *
         * Widget View Path
         *
         * @var string $view
         */

        protected $view = "avored-featured::widget.index";


        /**
         *
         * Widget Label
         *
         * @var string $view
         */

        protected $label = 'Featured List';


        /**
         *
         * Widget Type
         *
         * @var string $view
         */

        protected $type = "cms";

        /**
         *
         * Widget unique identifier
         *
         * @var string $identifier
         */
        protected $identifier = "avored-featured";


        public function view()
        {
            return $this->view;
        }

        /*
         * Widget unique identifier
         *
         */
        public function identifier()
        {

            return $this->identifier;
        }

        /*
        * Widget unique identifier
        *
        */
        public function label()
        {

            return $this->label;
        }

        /*
        * Widget unique identifier
        *
        */
        public function type()
        {

            return $this->type;
        }

        /**
         * View Required Parameters
         *
         * @return array
         */
        public function with()
        {

            return [];

        }

        public function render() {

            $productRepository = new Product();

            $featuredProperty = $productRepository->propertyModel()->whereIdentifier('avored-is-featured')->first();

            $featuredProductIds = ProductPropertyIntegerValue::wherePropertyId($featuredProperty->id)->paginate(4)->pluck('product_id');

            $products = new Collection();

            foreach ($featuredProductIds as $featuredProductId) {
                $products->push($productRepository->model()->find($featuredProductId));
            }

           // $products = $productRepository->model()->paginate(4);
            return view($this->view())->with('products' , $products);
        }

    }
