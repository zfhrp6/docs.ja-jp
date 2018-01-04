---
title: "方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 18f575e9bae37b66526d7b61a641374266ba627b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスに接続して通信するには、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションに、サービス アドレス、バインディング構成、およびサービス コントラクトの詳細が必要です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーは通常、必要な属性型の前の登録から必要なコントラクトを取得しますが、これが適切でない場合もあります。 登録の代わりに、モニカーは、`wsdl` パラメーターまたは Metadata Exchange を使用し、`mexAddress` パラメーターを使用することによって、WSDL (Web Services Definition Language) ドキュメントの形でコントラクトの定義を取得できます。  
  
 これによって、セルの値の一部が Web サービスとの対話によって計算される Excel ワークシートの配布などのシナリオが可能になります。 このシナリオでは、ドキュメントを開く可能性があるすべてのクライアントにサービス コントラクト アセンブリを登録することが実現できない可能性があります。 `wsdl` パラメーターまたは `mexAddress` パラメーターによって、自己完結型のソリューションが可能になります。  
  
> [!NOTE]
>  要求と応答の改ざんまたはなりすましを防止するために、相互認証を使用する必要があります。 具体的には、応答している Metadata Exchange エンドポイントが目的の信頼されたパーティであることがクライアントに対して保証されることが重要です。  
  
## <a name="example"></a>例  
 MEX コントラクトと共にサービス モニカーを使用する例を次に示します。 次のコントラクトが設定されたサービスは、wsHttpBinding で公開されます。  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 リモート サービスに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成するとき、次の例に示すモニカーの文字列を使用できます。  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 クライアント アプリケーションの実行中に、クライアントは、指定された `WS-MetadataExchange` で `mexAddress` を実行します。 これによって、複数のサービスのアドレス、バインディング、およびコントラクトの詳細が返される可能性があります。 `address`、`contract`、`contractNamespace`、`binding`、および `bindingNamespace` の各パラメーターは、目的のサービスを識別するために使用されます。 このパラメーターが一致した場合、モニカーは、適切なコントラクト定義を使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成します。これによって、型指定されたコントラクトと同様、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを使用して呼び出しを実行できるようになります。  
  
> [!NOTE]
>  モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。 このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
## <a name="see-also"></a>参照  
 [方法 : サービス モニカーを登録および構成する](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
