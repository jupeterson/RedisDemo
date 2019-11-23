FROM microsoft/dotnet:3.0-sdk as build

ARG BUILDCONFIG=RELEASE
ARG VERSION=1.0.0

COPY  RedisDemo.csproj /build/
RUN dotnet restore ./build/RedisDemo.csproj

COPY . ./build/
WORKDIR /build/

RUN dotnet publish ./RedisDemo.csproj -c $BUILDCONFIG -o out /p:Version=$VERSION

FROM microsoft/dotnet:3.0-aspnetcore-runtime
WORKDIR /app

COPY --from=build /build/out .

ENTRYPOINT ["dotnet", "RedisDemo.dll  "]