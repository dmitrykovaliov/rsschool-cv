# Dmitry Kovaliov
#### Minsk, Belarus

mob. +375 29 1017747, email [dmi.kovaliov@gmail.com](mailto:dmi.kovaliov@gmail.com)

* Present status: 
	* Junior Software Engineer, Epam
	
* Main skills:
	* Java
	* JS
	* React
	
* Tools:
	* Intellij Idea
	* VS Code
	* Junit
	
* English level:
	* B1+

* Goal:
	* Improve knowledge in Kotlin, Android OS, Android framework.
	In comparison with Java development in Android you have as support Google Team providing cool, modern features, which makes work of developer more focused and productive.

* Last features:
	* search for opt-out agreements
	* recent search
	
* Code examples (last two tasks):
    * ```java
      private String getDefaultLogoutURL(ZUiPage zPage, Company userCompany) {
        boolean isMobile = WebUtils.isCordovaMobile(zPage.getRequest());
        String defaultLogout = userCompany.getDefaultLogout();
    
        if (isMobile && !StringUtils.isBlank(defaultLogout)) {
          try {
            return new URIBuilder(defaultLogout)
                .setParameter(MercuryUtil.RETURN_TO_PARAM, "1")
                .toString();
          } catch (URISyntaxException e) {
            return defaultLogout;
          }
        }
        return defaultLogout;
      }
    ```
    
    * ```java
      public class EndPoint_NavigationTabs_Get implements EndPoint {
        private static final String PRM_ID = "set_name";
        private static final int HMENU_IS_PINNED_VALUE = 1;
        private static final String HMENU_PIN_ID = "HAMBURGER_MENU_PIN";
        private EndPointDescription description;
        private final ScreenLayoutHome screenLayoutHome;
      
        public EndPoint_NavigationTabs_Get() {
          screenLayoutHome = ScreenLayoutHome.getInstance();
          description = new EndPointDescription();
          description.consume(MediaType.APPLICATION_JSON_TYPE);
          description.produce(MediaType.APPLICATION_JSON_TYPE);
          description.addParameter(EndPointParameter.path(PRM_ID).asEnum(TabSetEnum.class).required());
        }
      
        @Override
        public EndPointDescription getDescription() {
          return description;
        }
      
        @Override
        public Result process(Context context, Request request, Response response) throws IOException {
      
          String setName = request.getPathParameter(PRM_ID);
          UserConnection userConnection = context.getUserConnection();
      
          ScreenLayout tabScreenLayout =
              screenLayoutHome.findUserLayoutByName(userConnection, setName, true);
          ScreenLayout pinScreenLayout =
              screenLayoutHome.findUserLayoutByName(userConnection, HMENU_PIN_ID, true);
      
          if (tabScreenLayout == null || pinScreenLayout == null) {
            return Results.notFound(ZMessage.getError("@@Navigation.MenuElementNotFound"));
          }
      
          TabSetDTO tabSetDTO =
              new TabSetDTO(
                  tabScreenLayout.getSelectedTab(),
                  HMENU_IS_PINNED_VALUE == pinScreenLayout.getSelectedTab());
      
          return Results.ok(tabSetDTO);
        }
      }
      ```
	
