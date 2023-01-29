<div class="body">
    <div class="card-grid">
        <div class="card">
            <div class="AEAC">
                <div class="card-body">
                    <a href="./AEAC">
                        <button class="btn"> AEAC </button>
                    </a>
                </div>
            </div>
        </div>

        <div class="card">
            <div class="SUAS">
                <div class="card-body">
                    <a href="./SUAS">
                        <button class="btn"> SUAS </button>
                    </a>
                </div>
            </div>
        </div>
    </div>
</div>

<style>
    .card-grid {
        display: grid;
        grid-column: repeat(auto-fit(), minmax(300px, 1fr));
        align-items: center;
        justify-content: center;
    }
    .card {
        background-color: white;
        border: 1px solid black;
        border-radius: 40px 30px;
        padding: 1rem;
        margin-bottom: 2em;
        border: none;
        box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.2);
    }

    .btn {
        border: none;
        width: 250px;
        height: 90px;
        border-radius: 50px;
        cursor: pointer;
        font-size: 40px;
        text-transform: uppercase;
        letter-spacing: 10px;
        font-weight: bold;
        box-shadow: 0 8px 10px rgba(0, 0, 0, 0.1);
        transition: box-shadow 0.3s ease, background-color 0.3s ease, color 0.3s ease;
    }
    .btn:hover {
        background-color: #2da0dc;
        transform: translateY(-7px);
        color: #fff;
        box-shadow: 0px 10px 15px rgba(46, 223, 229, 0.4);
    }
</style>
