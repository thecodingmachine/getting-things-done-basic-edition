Writing a datagrid
==================

Mouf's "Getting things done" comes with [Evolugrid, a flexible Ajax table you can use to display your data](http://mouf-php.com/packages/mouf/html.widgets.evolugrid).
You can check the full [Evolugrid documentation](http://mouf-php.com/packages/mouf/html.widgets.evolugrid), or have a look at the quick tutorial below.

In this tutorial, we will assume you already know how to [write a controller](writing_a_controller.md) and how to [use TDBM daos](regenerating_daos.md).

Let's assume we have a database with a "clients" table.

<table class="table">
	<tr>
		<th>id</th>
		<th>name</th>
		<th>first_name</th>
		<th>email</th>
	</tr>
	<tr>
		<td>1</td>
		<td>Doe</td>
		<td>John</td>
		<td>john@doe.com</td>
	</tr>
	<tr>
		<td>2</td>
		<td>Durand</td>
		<td>Jim</td>
		<td>jim.durant@mymail.com</td>
	</tr>
	<tr>
		<td>...</td>
		<td>...</td>
		<td>...</td>
		<td>...</td>
	</tr>
</table>

Let's say we want to display this table in an Ajax grid, with pagination and filtering on the name and first_name columns, and a link to an "edit" form (we will not develop the edit form as part of this tutorial).

Here is the process to develop this grid

- Create a controller
- Create one action for the web page that contains the grid (with the matching view)
- Create the evolugrid in Mouf and bind it to the controller
- Create one action for the Ajax URL that will return JSON data
- Query the database and generate the JSON data

Creating the controller
-----------------------

We will go quickly through the creation of the controller. This is already covered by the [writing a controller tutorial](writing_a_controller.md).

The file structure should be this:

- src
	- Test
		- Controllers
			- ClientsController.php
	- views
		- clients_list.php

In this controller, we will add a field containing the Evolugrid, and the DaoFactory to access the database:


### Controller: ClientsController.php
```php
<?php
namespace Test\Controllers;

use Mouf\Html\Widgets\EvoluGrid\EvoluGrid;
use Bilal\Dao\DaoFactory;
use Mouf;
use Mouf\Html\HtmlElement\HtmlBlock;
use Mouf\Html\Template\TemplateInterface;
use Mouf\Mvc\Splash\Controllers\Controller;

/**
 * This controller is in charge of displaying a list of clients.
 */
class ClientsController extends Controller
{
	/**
	 * The content block.
	 * @var HtmlBlock
	 */
	public $content;
	
	/**
	 * The template.
	 * @var TemplateInterface
	 */
	public $template;
	
	/**
	 * Factory used to access the database tables.
	 * @var DaoFactory
	 */
	public $daoFactory;
	
	/**
	 * The grid displaying the list of clients
	 * @var EvoluGrid
	 */
	public $clientsGrid;
	
	/**
	 * Displays the list of all clients
	 * 
	 * @Get
	 * @URL clients/list
	 */
	public function index() {
		$this->template->setTitle("Clients list");
		$this->content->addFile(__DIR__."/../../views/clients_list.php", $this);
		$this->template->toHtml();
	}
}
```

### View: clients_list.php
```php
<?php /* @var $this Test\Controllers\ClientsController */ ?> 

<h1>Clients list</h1>
<?php
$this->mealsGrid->toHtml();
?>
```

Declaring controller and Evolugrid instances
--------------------------------------------

We will now declare the instances for our sample.


