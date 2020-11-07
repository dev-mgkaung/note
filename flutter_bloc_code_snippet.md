# Flutter Bloc Code Snippet

## main.dart

```python
class MyApp extends StatefulWidget {

  @override
  State<StatefulWidget> createState()=> MyAppState();

}

class MyAppState extends State<MyApp>{

  @override
  Widget build(BuildContext context) {

           return Container(  
                    child: MultiRepositoryProvider(

                        providers: [
                          RepositoryProvider(create: (context) => NetworkServiceRepository()),
                          RepositoryProvider(create: (context) => CartDatabaseRepository()),
                          RepositoryProvider(create: (context) => ChectoutDatabaseRepository())
                                   ],
                                   
                        child:  MultiBlocProvider(
                          providers: [

                        BlocProvider<AccountBloc>(
                        create: (BuildContext context) => AccountBloc(context.repository<ECommerceAPI>()),
                        ),

                        BlocProvider<PaymentBloc>(
                        create: (BuildContext context) => PaymentBloc(context.repository<PaymentCardRepository>()),
                        )
                                      ],
                     child:     MaterialApp(
                      localizationsDelegates: [
                      GlobalMaterialLocalizations.delegate,
                      GlobalWidgetsLocalizations.delegate,
                      SpecificLocalizationDelegate()
                     ],
                     supportedLocales: [
                      const Locale('en','US'),
                      const Locale('my','')
                      ],
                     locale: languageProvider.appLocal,
                     title: title,
                     theme: themeProvider.getThemeData,
                     home: SplashScreen(),
                     debugShowCheckedModeBanner: false,
                  ),
                )));
                                   );
```
