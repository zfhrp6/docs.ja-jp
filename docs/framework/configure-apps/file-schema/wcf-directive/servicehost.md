---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 027debb311a3f9547623b6dff778e82b7e475327
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="servicehost"></a>@ServiceHost
サービス ホストの生成に使用されるファクトリを、ホストされるサービスと、.svc ファイルで提供されるホスティング コードのアクセスとコンパイルに必要なその他のプログラミング部分に関連付けます。  
  
## <a name="syntax"></a>構文  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>属性  
  
#### <a name="service"></a>サービス  
 ホストされるサービスの CLR 型名。 これは、1 つ以上のサービス コンタクトを実装する型の修飾名にする必要があります。  
  
#### <a name="factory"></a>ファクトリ  
 サービス ホストのインスタンス化に使用されるサービス ホスト ファクトリの CLR 型名。 この属性は省略できます。 未指定の場合は、<xref:System.ServiceModel.Activation.ServiceHostFactory> のインスタンスを返す既定の <xref:System.ServiceModel.ServiceHost> が使用されます。  
  
#### <a name="debug"></a>デバッグ  
 デバッグ シンボルを使用して [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスをコンパイルするかどうかを示します。 デバッグ シンボルを含む `true` サービスをコンパイルする場合は [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]、それ以外の場合は `false` を指定します。  
  
#### <a name="language"></a>言語  
 ファイル (.svc) 内のすべてのインライン コードをコンパイルするときに使用する言語を指定します。 値は、C#、VB、JS (それぞれ、C#、Visual Basic .NET、および JScript .NET を示す) など、.NET がサポートする任意の言語を表します。 この属性は省略できます。  
  
#### <a name="codebehind"></a>CodeBehind  
 XML Web サービスを実装するクラスが同じファイル内に存在せず、アセンブリとしてコンパイルされずに \Bin ディレクトリに置かれているとき、XML Web サービスを実装するソース ファイルを指定します。  
  
## <a name="remarks"></a>コメント  
 サービスのホストに使用される <xref:System.ServiceModel.ServiceHost> は、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] プログラミング モデル内の拡張ポイントです。 ファクトリ パターンは、ホスティング環境が直接インスタンス化できないポリモーフィック型の可能性があるため、<xref:System.ServiceModel.ServiceHost> のインスタンス化に使用されます。  
  
 既定の実装では <xref:System.ServiceModel.Activation.ServiceHostFactory> を使用して、<xref:System.ServiceModel.ServiceHost> のインスタンスを作成します。 (1 つを派生ホストを返す)、独自のファクトリを指定するには、ファクトリの実装での CLR 型名を指定することによって、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブです。  
  
 既定のファクトリではなく独自のカスタム サービス ホスト ファクトリに使用する、型の名前を指定だけ、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブが次のようにします。  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 ファクトリ実装はできるだけ軽量に保持してください。 多くのカスタム ロジックがある場合は、それらのロジックをファクトリ内部ではなくホスト内部に置くとコードがさらに再利用可能になります。  
  
 例については、AJAX 対応エンドポイントを有効にする`MyService`、指定、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>の値を`Factory`属性で、既定ではなく、<xref:System.ServiceModel.Activation.ServiceHostFactory>で、 [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)としてディレクティブ次の例に示します。  
  
## <a name="example"></a>例  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>参照  
 [カスタム サービス ホスト](../../../../../docs/framework/wcf/samples/custom-service-host.md)
