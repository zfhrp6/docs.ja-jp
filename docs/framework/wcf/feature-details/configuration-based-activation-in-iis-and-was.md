---
title: "IIS と WAS における構成ベースのアクティブ化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0938b98a3f079d03653df55f10c26a4a62db5bf3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a>IIS と WAS における構成ベースのアクティブ化
インターネット インフォメーション サービス (IIS: Internet Information Services) または Windows プロセス アクティブ化サービス (WAS) で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストする場合は、.svc ファイルを用意する必要があります。 .svc ファイルには、サービスの名前と、オプションのカスタム サービス ホスト ファクトリが含まれています。 この追加ファイルによって、管理のオーバーヘッドが増加します。 構成ベースのアクティブ化機能により、.svc ファイルを用意する必要がなくなり、関連するオーバーヘッドも発生しません。  
  
## <a name="configuration-based-activation"></a>構成ベースのアクティブ化  
 構成ベースのアクティブ化では、以前は .svc ファイルに配置されていたメタデータを受け取り、それを Web.config ファイルに配置します。 内で、<`serviceHostingEnvironment`> 要素は、<`serviceActivations`> 要素。 内で、<`serviceActivations`> 要素が 1 つ以上 <`add`> 要素、各ホステッド サービスに 1 つです。 <`add`> 要素には属性の場合、サービスおよびサービスの種類、サービス ホスト ファクトリの相対アドレスを設定することができます。 次の構成コード例は、このセクションの使用方法を示しています。  
  
> [!NOTE]
>  各 <`add`> 要素には、サービスまたは factory 属性を指定する必要があります。 サービスとファクトリ属性の両方を指定することもできます。  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 このコードを Web.config ファイルに含めると、サービス ソース コードをアプリケーションの App_Code ディレクトリに配置するか、コンパイル済みアセンブリをアプリケーションの Bin ディレクトリに配置することができます。  
  
> [!NOTE]
>  -   構成ベースのアクティブ化機能を使用する場合、.svc ファイルのインライン コードはサポートされません。  
> -   `relativeAddress`属性をなどの相対アドレスに設定する必要があります"\<サブディレクトリ >/service.svc"または"~/\<directory サブ/service.svc"です。  
> -   WCF と関連付けられている既知の拡張子を持たない相対アドレスを登録すると、構成例外がスローされます。  
> -   指定された相対アドレスは、仮想アプリケーションのルートが基準になります。  
> -   構成の階層的モデルにより、コンピューター レベルおよびサイト レベルの登録された相対アドレスは、仮想アプリケーションによって継承されます。  
> -   構成ファイル内での登録は、.svc、.xamlx、.xoml、またはその他のファイルでの設定よりも優先されます。  
> -   IIS/WAS に送信された URI 内の \ (円記号) は、自動的に / (スラッシュ) に変換されます。 \ を含む相対アドレスが追加され、その相対アドレスを使用する URI を IIS に送信した場合は、円記号がスラッシュに変換されるため、IIS では、それを相対アドレスと一致させることができません。 IIS は、一致するものが見つからなかったことを示すトレース情報を送信します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)  
 [ホスト ワークフロー サービスの概要](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
