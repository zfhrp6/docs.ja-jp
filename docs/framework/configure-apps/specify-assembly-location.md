---
title: "アセンブリ &#39; の指定の場所"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4cfe8752ce3a562e1e4b576c63b56ff56255ff62
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="specifying-an-assembly39s-location"></a>アセンブリ &#39; の指定の場所
これにはアセンブリの場所を指定する 2 つの方法があります。  
  
-   使用して、 [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)要素。  
  
-   使用して、 [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)要素。  
  
 使用することも、 [.NET Framework 構成ツール (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764)をアセンブリの場所を指定するか、共通言語ランタイム アセンブリを探すための場所を指定します。  
  
## <a name="using-the-codebase-element"></a>使用して、 \<codeBase > 要素  
 使用することができます、  **\<codeBase >**のみマシン構成ファイルまたはパブリッシャー ポリシー ファイルでもアセンブリのバージョンをリダイレクトする要素。 ランタイムは、使用するアセンブリ バージョンを判断した場合は、バージョンを決定する、ファイルからコード ベース設定が適用されます。 コード ベースが指定されていない場合、ランタイムは、通常の方法で、アセンブリをプローブします。 詳細については、「[ランタイム アセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)です。  
  
 次の例では、アセンブリの場所を指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **バージョン**属性が必要ですがすべて厳密な名前のアセンブリのアセンブリの厳密な名前が付いていない場合は省略されます。 **\<CodeBase >**要素が必要です、 **href**属性。 バージョン範囲を指定することはできません、  **\<codeBase >**要素。  
  
> [!NOTE]
>  厳密な名前ではないアセンブリ コード ベースのヒントを指定している場合、ヒントは、アプリケーション ベースまたはアプリケーション ベース ディレクトリのサブディレクトリを指す必要があります。  
  
## <a name="using-the-probing-element"></a>使用して、 \<probing > 要素  
 ランタイムが調査で基本コードを持たないアセンブリを検索します。 調査の詳細については、次を参照してください。[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)です。  
  
 使用することができます、 [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)アプリケーション構成ファイルの要素をランタイムがアセンブリを検索するときに検索するサブディレクトリを指定します。 次の例では、ランタイムが検索するディレクトリを指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath**属性には、ランタイムがアセンブリを検索するディレクトリが含まれています。 アプリケーションが C:\Program files \myapp にある場合は、ランタイムは C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin および C:\Program Files\MyApp\Bin3 でコード ベースが指定されていないアセンブリを検索します。 指定したディレクトリ**privatePath**アプリケーション ベース ディレクトリのサブディレクトリにある必要があります。  
  
## <a name="see-also"></a>参照  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [.NET Framework アプリの構成](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
