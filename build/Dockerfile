FROM dart:stable AS build
WORKDIR /app
COPY . .
RUN sed -i 's/InternetAddress.anyIPv6/InternetAddress.anyIPv4/g' bin/server.dart
RUN dart pub get && dart compile exe bin/server.dart -o /app/server

FROM scratch
COPY --from=build /runtime/ /
COPY --from=build /app/server /app/server
ENV PORT=8080
EXPOSE 8080
CMD ["/app/server"]
