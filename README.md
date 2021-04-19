# CI_Migration



Open application/config/migration.php file and set the value for $config['migration_enabled'] from false to true.

Create a folder called migrations in application/config/ folder and that's it.

create a file called 001_add_users.php in migrations folder

Now that we have created our migration, we need to run it. Let's create a controller called Migrate that will run our migrations:


<?php

class migrate extends CI_Controller {
    public function index()
    {
        // load migration library
        $this->load->library('migration');

        if ( ! $this->migration->current())
        {
            echo 'Error' . $this->migration->error_string();
        } else {
            echo 'Migrations ran successfully!'
        }   
    }    
}


Now if you visit your application url at http://yoursite.com/migrate and all goes well, you should success message and the new table users should be created in the database.
