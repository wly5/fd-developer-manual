Introduction
============

One of the main features of Freedomotic is its plugin-based
architecture. A plugin allow to integrate any hardware, object or device
in Freedomotic just with a simple configuration.

Thanks to the Freedomotic modular feature, anyone could create his own
"Marketplace" (http://freedomotic.com/plugins) or plugin package
provider, from where the integrator could download and install the
plugins packages easily. Also, any provider could be combined with the
others, so the user doesn't need to search in several different places.

A MarketPlace Provider, could be a web page, an ftp, a local directory,
any place in which a package with the Freedomotic format could be stored
and be accessible.

Details
=======

Freedomotic comes with an already deployed provider that acces to the
MarketPlace? in the main page of Freedomotic:

http://www.freedomotic.com/plugins

Steps to create a provider using Netbeans:
------------------------------------------

1. Create a new class project for our provider.
2. Include the library org-openide-util-lookup.jar This library is
   already included with the Netbeans installation and could be found in
   the path: NETBEANSDIR/platform/lib/org-openide-util-lookup.jar.
   However, it is also include in the trunk/lib/core directory of the
   freedomotic repository.
3. Create a new basic class in java. This class must extends
   IMarketPlace, alse we must use the Java decorators so Netbeans could
   create the correct files in META-INF when the project is build.
   \`\`\`java import org.openide.util.lookup.ServiceProvider; import
   com.freedomotic.service.IMarketPlace; import
   com.freedomotic.service.PluginPackage; import java.util.ArrayList;

   @ServiceProvider(service = IMarketPlace.class) public class
   FreedomoticMarketPlace implements IMarketPlace{

   public FreedomoticMarketPlace() {

   }

   @Override public ArrayList getAvailablePackages() { //TO BE developed
   }

   @Override public void updatePackageList() { //TO BE developed }

} \`\`\` The last thing to do is to fill the methods that retrieve the
plugin information.

Provider Deployment
===================

To install the provider in Freedomotic is as easy as just build and copy
the .jar file and libraries to the directory /plugins/providers/ (the
libraries must be copied to /plugins/providers/lib) The next time
Freedomotic starts, the provider will be available.
