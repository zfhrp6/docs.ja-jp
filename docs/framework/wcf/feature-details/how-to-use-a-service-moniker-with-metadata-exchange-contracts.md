---
title: '方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491251"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a>方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する
新しい WCF サービスを開発した後にスクリプトまたは Visual Basic 6.0 アプリケーションからこれらのサービスを呼び出せるようにすることもできます。 1 つのメソッドは、WCF クライアント アセンブリを生成、COM にアセンブリを登録、アセンブリを GAC にインストール、および Visual Basic コードから COM の型を参照することです。 アプリケーションを配布するときに、WCF クライアント アセンブリもを配布する必要があります。 次にユーザーは COM を使用して WCF クライアント アセンブリを登録し、それを GAC に配置する必要があります。 WCF の COM 相互運用機能を使用すると、WCF クライアント アセンブリに依存せず、同じサービス呼び出しを行うこともできます。 WCF モニカーでは、metadata exchange (Mex) エンドポイント サービス モニカーを使用して型を抽出する URI を指定することで任意の COM 互換言語 (Visual Basic、VBScript、Visual Basic for Applications (VBA) やなど) からすべての WCF サービスを呼び出すことができます。サービスに関する情報。 このトピックでは、Mex エンドポイントを指定する WCF モニカーを使用して WCF の入門サンプルを呼び出す方法について説明します。  
  
> [!NOTE]
>  WCF クライアント アセンブリで定義された型が実際にはインスタンス化します。 アセンブリはメタデータにのみ使用されます。  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a>Mex アドレスを使うサービス モニカーの使用  
  
1.  この入門サンプルをビルドし、Internet Explorer を使用して、その URL を参照 (http://localhost/ServiceModelSamples/Service.svc)サービスが動作していることを確認します。  
  
2.  Visual Basic スクリプトまたは Visual Basic アプリケーションを作成し、次のコードを記述します。  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  作成した Visual Basic アプリケーションまたはスクリプトを実行します。  
  
    > [!NOTE]
    >  モニカーがサービスのメタデータを読み取るには、呼び出すサービスで、Mex エンドポイントが公開されている必要があります。 詳細については、次を参照してください。[する方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)です。  
  
    > [!NOTE]
    >  モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。  このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
## <a name="see-also"></a>関連項目  
 [方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [方法 : WSDL コントラクトと共にサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
