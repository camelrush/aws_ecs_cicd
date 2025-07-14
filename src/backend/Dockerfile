# .NET 9.0 SDK イメージを使用してビルドステージを開始
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app

# プロジェクトファイルのみを先にコピーして、依存関係のキャッシュを有効化
COPY backend.csproj ./
# 依存関係を復元（NuGet パッケージの取得）
RUN dotnet restore

# 残りのすべてのファイルをコピー
COPY . ./
# リリース構成でプロジェクトをパブリッシュし、出力を out フォルダへ
RUN dotnet publish "backend.csproj" -c Release -o out

# ランタイムステージ（本番用の軽量なイメージ）
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
# ビルドステージから成果物をコピー
COPY --from=build /app/out .

# アプリがリッスンするURLを環境変数で指定（httpのポート80）
ENV ASPNETCORE_URLS="http://+:80"
EXPOSE 80

# アプリケーションを起動
ENTRYPOINT ["dotnet", "backend.dll"]
