see [Create a generator](https://github.com/sr57/laravel-blueprint-faq/tree/master/Create%20a%20generator) for generality

```
    public function output(Tree $tree): array
    {
        $output = [];      
 		    $stub="";			# empry for this simple example
        foreach ($tree->controllers() as $controller) {
            if (!$controller->isApiResource()) {
                $path = $this->outputPath($controller->name());

                $this->files->put($path, $this->populateStub($stub, $this->yajra($controller->name())));
                $output['created'][] = $path;
            }
        }    
        return $output;
    } # End of output

    protected function outputPath($name): string
    {
        $path = "app/Http/Controllers/$name"."Controller.php";

        if (!$this->files->exists(dirname($path))) {
            $this->files->makeDirectory(dirname($path), 0755, true);
        }
        return $path;
    }
    
   
    protected function populateStub(string $stub, $code): string
	    	$stub=str_replace('{{ body }}',$code,$stub);
        return $stub;
    }
    
    public function types(): array
    {
		# nécessaire sinon error "abstract method must be declared" - Utiilité
        return ['Yajra'];
    } 
    
    protected function yajra($name) {
		  $Model=$name;			# assuming Controller name = Model name
	  	$model=strtolower($Model);
		  $code="
        return 'Yajra\Datatables\Datatables'::of($Model::query())
			  ->make(true);
";
        return $code;
	}
```
