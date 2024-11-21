# ベースイメージとしてOpenJDK 17を使用
FROM openjdk:21-jdk-slim

# Mavenをインストール
RUN apt-get update && apt-get install -y maven

# 作業ディレクトリを設定
WORKDIR /src

# Mavenの設定ファイルとソースコードをコピー
COPY pom.xml .
COPY src ./src

# Mavenでパッケージをビルド（テストをスキップ）
RUN mvn clean package -DskipTests

# アプリケーションを起動
CMD ["java", "-jar", "target/demo-0.0.1-SNAPSHOT.jar"]

# ポートを公開
EXPOSE 8080