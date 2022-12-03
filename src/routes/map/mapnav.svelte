<head>
    <!-- FontAwesome 6.2.0 CSS -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css"
        integrity="sha512-xh6O/CkQoPOWDdYTDqeRdPCVd1SpvCA9XXcUnZS2FmJNp1coAFzvtCN9BmamE+4aHK8yyUHUSCcJHgXloTyT2A=="
        crossorigin="anonymous" referrerpolicy="no-referrer" />
    
    <!-- (Optional) Use CSS or JS implementation -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/js/all.min.js"
        integrity="sha512-naukR7I+Nk6gp7p5TMA4ycgfxaZBJ7MO5iC3Fp6ySQyKFHOGfpkSZkYVWV5R7u7cfAicxanwYQ5D1e17EfJcMA=="
        crossorigin="anonymous" referrerpolicy="no-referrer"></script>

        		<!--Bootstrap-->
		<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
</head>
<!---------------->
<script>

	
</script>
<!---------------->
<nav class="navbar navbar-expand navbar-light bg-light">
    <ul class="nav navbar-nav" id="nav">
        <li class="nav-item">
            <a class="nav-link active" href="#1" aria-current="page">Flight Data <span class="visually-hidden">(current)</span></a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="#2">Flight Plan</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="#3">Intial Setup</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="#4">Configure</a>
        </li>
        <li class="nav-item">
            <a class="nav-link" href="#5">Simulation</a>
        </li>
  
        <li class="nav-item right">
            <div class="dropdown">
                <button class="btn dropdown-toggle" type="button" id="triggerId" data-bs-toggle="dropdown" aria-haspopup="true"
                        aria-expanded="false" style="background-color: #BECAD3;">
                            Controls
                        </button>
                <div class="dropdown-menu" aria-labelledby="triggerId">
                    <a class="dropdown-item" href="#6">Lock</a>
                    <a class="dropdown-item" href="#7">Unlock</a>
                </div>
            </div>
        </li>

        <li class="nav-item">
            <div class="dropdown">
                <button class="btn dropdown-toggle" type="button" id="triggerId" data-bs-toggle="dropdown" aria-haspopup="true"
                        aria-expanded="false" style="background-color: #BECAD3;">
                            Connect
                        </button>
                <div class="dropdown-menu" aria-labelledby="triggerId">
                    <a class="dropdown-item" href="#6">Ataksak</a>
                    <a class="dropdown-item" href="#7">Condor</a>
                </div>
            </div>
        </li>
        <li>
            <i class="fa fa-link fa-lg" aria-hidden="true" id="linklogo"></i>
        </li>
    </ul>
</nav>

<!---------------->
<style>
nav{
    border-radius: 10px;
}

#nav{
    min-width: 100%;
}

.nav-item{
    padding: 0 1em;
}

.right{
    margin-left: auto;
}

#linklogo{
    margin-top: 0.5em;
    margin-right: 0.5em;
}

.controls{
    margin-left: auto;
}
</style>
