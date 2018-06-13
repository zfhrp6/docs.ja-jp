---
title: '方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: fd61528770b16b13430be3691aef19c1cc743e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497972"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する
接続し、Windows Communication Foundation (WCF) サービスとの通信、WCF クライアント アプリケーションには、サービス アドレス、バインディング構成と、サービス コントラクトの詳細が必要です。  
  
 WCF サービス モニカーは通常、必要な属性型の前の登録から必要なコントラクトを取得しますが、ここでこれを実現できない場合がある可能性があります。 登録の代わりに、モニカーは、`wsdl` パラメーターまたは Metadata Exchange を使用し、`mexAddress` パラメーターを使用することによって、WSDL (Web Services Definition Language) ドキュメントの形でコントラクトの定義を取得できます。  
  
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
  
 リモート サービス モニカー文字列の例を次の WCF クライアントを構築するために使用できます。  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 クライアント アプリケーションの実行中に、クライアントは、指定された `WS-MetadataExchange` で `mexAddress` を実行します。 これによって、複数のサービスのアドレス、バインディング、およびコントラクトの詳細が返される可能性があります。 `address`、`contract`、`contractNamespace`、`binding`、および `bindingNamespace` の各パラメーターは、目的のサービスを識別するために使用されます。 これらのパラメーターが一致した場合とモニカーは、適切なコントラクト定義を使用する WCF クライアントを構築が、呼び出される WCF クライアントを使用して、型指定されたコントラクトと同様。  
  
> [!NOTE]
>  モニカーの形式が正しくないか、サービスを使用できない場合は、`GetObject` を呼び出すと、"構文が無効です" というエラーが返されます。 このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [方法 : サービス モニカーを登録および構成する](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
