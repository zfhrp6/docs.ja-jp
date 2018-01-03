---
title: "方法 : DEVPATH を使用してアセンブリを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4ee4200a67ef9d9d123be3bc32b02ac61512d23b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>方法 : DEVPATH を使用してアセンブリを指定する
開発者は、複数のアプリケーションの構築、共有アセンブリが正常に動作するかどうかを確認する可能性があります。 開発サイクル中に、グローバル アセンブリ キャッシュにアセンブリを配置継続的に、代わりに、開発者は、アセンブリのビルド出力ディレクトリを指す DEVPATH 環境変数を作成できます。  
  
 たとえば、MySharedAssembly と呼ばれる共有アセンブリをビルドして、出力ディレクトリは C:\MySharedAssembly\Debug です。 C:\MySharedAssembly\Debug は DEVPATH 変数にすることができます。 指定する必要がありますし、 [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)マシン構成ファイル内の要素。 この要素は、アセンブリの検索に DEVPATH を使用する共通言語ランタイムに指示します。  
  
 共有アセンブリは、ランタイムによって探索可能にする必要があります。  アセンブリ参照の使用を解決するためのプライベート ディレクトリを指定する、 [ \<codeBase > 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)または[ \<probing > 要素](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)」の説明に従って、構成ファイルで[アセンブリの場所を指定する](../../../docs/framework/configure-apps/specify-assembly-location.md)です。  アプリケーションのディレクトリのサブディレクトリに、アセンブリを格納することもできます。 詳細については、「 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
> [!NOTE]
>  これは開発専用の高度な機能です。  
  
 次の例では、DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索するランタイムを発生させる方法を示します。  
  
## <a name="example"></a>例  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 この設定の既定値は false。  
  
> [!NOTE]
>  この設定を使用して、開発時のみです。 ランタイムは、DEVPATH で見つかった厳密な名前のアセンブリのバージョンをチェックしません。 最初に見つかったアセンブリは単に使用します。  
  
## <a name="see-also"></a>参照  
 [.NET Framework アプリの構成](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
