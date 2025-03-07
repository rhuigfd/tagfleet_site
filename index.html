<?php
// Connexion à la base de données
$conn = new mysqli("172.21.3.41", "administrateur", "TagFleet@Admin#11", "serveurBDD");

if ($conn->connect_error) {
    die("Connexion échouée: " . $conn->connect_error);
}

// Ajouter un contenu
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST["ajouter_contenu"])) {
    $nom_contenu = $_POST["nom_contenu"];
    $type = $_POST["type"]; // Ajout du champ type
    $id_ancres = $_POST["id_ancres"];
    $file_name = basename($_FILES["fichier"]["name"]);
    $target_dir = "uploads/";
    $file_extension = strtolower(pathinfo($file_name, PATHINFO_EXTENSION));
    $allowed_extensions = ["jpg", "jpeg", "png"];

    if (!in_array($file_extension, $allowed_extensions)) {
        echo "<script>alert('Format de fichier non autorisé. Formats acceptés: jpg, jpeg, png.');</script>";
    } else {
        // Créer le dossier s'il n'existe pas
        if (!is_dir($target_dir)) {
            mkdir($target_dir, 0777, true);
        }

        if (move_uploaded_file($_FILES["fichier"]["tmp_name"], $target_dir . $file_name)) {
            // Laisser MySQL générer automatiquement l'ID de contenu
            // Pas besoin de passer l'ID ici, il est auto-généré
            $stmt = $conn->prepare("INSERT INTO Contenus (nom, type, id_ancres, image) VALUES (?, ?, ?, ?)");
            $stmt->bind_param("ssis", $nom_contenu, $type, $id_ancres, $file_name);
            $stmt->execute();
            $stmt->close();

            header("Location: index.php");
            exit();
        } else {
            echo "<script>alert('Erreur lors de l\'upload du fichier.');</script>";
        }
    }
}

// Supprimer un contenu
if (isset($_GET["delete"])) {
    $id = (int) $_GET["delete"]; // Forcer en entier

    // Supprimer le contenu
    $stmt = $conn->prepare("DELETE FROM Contenus WHERE id_contenu = ?");
    $stmt->bind_param("i", $id); // L'ID est maintenant un entier
    $stmt->execute();
    $stmt->close();

    header("Location: index.php");
    exit();
}

// Récupérer toutes les ancres
$result_ancres = $conn->query("SELECT * FROM Ancres");

// Récupérer tous les contenus
$result_contenus = $conn->query("SELECT * FROM Contenus");
?>



<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestion des Ancres et Contenus</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
</head>
<body class="container mt-4">

    <h2 class="mb-4">Gestion des Contenus</h2>

    <!-- Formulaire d'ajout de contenu avec upload -->
    <form method="POST" enctype="multipart/form-data" class="mb-4">
        <div class="row g-2">
            <div class="col-md-3">
                <input type="text" name="nom_contenu" class="form-control" placeholder="Nom du contenu" required>
            </div>
            <div class="col-md-3">
                <input type="text" name="type" class="form-control" placeholder="Type de contenu" required>
            </div>
            <div class="col-md-3">
                <input type="file" name="fichier" class="form-control" required>
            </div>
            <div class="col-md-2">
                <select name="id_ancres" class="form-control" required>
                    <option value="">Sélectionner une ancre</option>
                    <?php
                    // Réinitialiser le pointeur de la table des ancres
                    $result_ancres->data_seek(0); 
                    while ($ancre = $result_ancres->fetch_assoc()): ?>
                        <option value="<?= $ancre['id_ancres'] ?>">
                            <?= $ancre['nom'] ?> (<?= $ancre['description'] ?>, X: <?= $ancre['x'] ?>, Y: <?= $ancre['y'] ?>)
                        </option>
                    <?php endwhile; ?>
                </select>
            </div>
            <div class="col-md-1">
                <button type="submit" name="ajouter_contenu" class="btn btn-primary w-100">Ajouter</button>
            </div>
        </div>
    </form>

    <!-- Tableau des Contenus -->
    <table class="table table-bordered">
        <thead class="table-dark">
            <tr>
                <th>Nom</th>
                <th>Type</th>
                <th>Image</th>
                <th>Ancre Associée</th>
                <th>Actions</th>
            </tr>
        </thead>
        <tbody>
            <?php while ($contenu = $result_contenus->fetch_assoc()): ?>
                <tr>
                    <td><?= $contenu["nom"] ?></td>
                    <td><?= $contenu["type"] ?></td>
                    <td>
                        <?php if (in_array(pathinfo($contenu['image'], PATHINFO_EXTENSION), ['jpg', 'jpeg', 'png', 'gif', 'pdf'])): ?>
                            <!-- Afficher l'image si c'est un fichier image -->
                            <img src="uploads/<?= $contenu['image'] ?>" alt="<?= $contenu['nom'] ?>" style="width: 100px; height: auto;">
                        <?php else: ?>
                            <!-- Afficher un lien vers le fichier si ce n'est pas une image -->
                            <a href="uploads/<?= $contenu['image'] ?>" target="_blank"><?= $contenu['image'] ?></a>
                        <?php endif; ?>
                    </td>
                    <td>
                        <?php
                        // Récupérer le nom de l'ancre associée
                        $ancre_assoc = $conn->query("SELECT nom FROM Ancres WHERE id_ancres = " . $contenu['id_ancres'])->fetch_assoc();
                        echo $ancre_assoc['nom'];
                        ?>
                    </td>
                    <td>
                        <a href="?delete=<?= $contenu['id_contenu'] ?>" class="btn btn-danger btn-sm" onclick="return confirm('Supprimer ce contenu ?')">Supprimer</a>
                    </td>
                </tr>
            <?php endwhile; ?>
        </tbody>
    </table>

    <!-- Image du magasin en bas -->
    <div class="text-center mb-4">
        <img src="plan magasin2.png" alt="Magasin" style="max-width: 100%; height: auto;">
    </div>

</body>
</html>
