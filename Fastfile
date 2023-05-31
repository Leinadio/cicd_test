default_platform(:android)

platform :android do
  lane :build_flutter_app do
    # Étape de construction de l'application Flutter
    sh "flutter clean"
    sh "flutter pub get"
    sh "flutter build apk --release" # Remplacez par "flutter build appbundle --release" pour générer un bundle d'application (.aab)
  end

  lane :deploy_to_firebase do
    # Étapes de construction de l'application Flutter
    flutter_build()

    # Étape de signature de l'application
    gradle(
      task: "assemble",
      build_type: "release"
    )

    # Étape de déploiement sur Firebase App Distribution
    firebase_app_distribution(
      app: "com.example.cicd_test",
      groups: "testygroup",
      release_notes: "Version 1.0.0",
      firebase_cli_token: ENV["FIREBASE_CLI_TOKEN"],
      debug: false
    )
  end
end