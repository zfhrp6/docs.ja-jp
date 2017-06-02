---
title: "方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する
新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをいくつか開発した後に、そのサービスをスクリプトまたは Visual Basic 6.0 アプリケーションから呼び出せるようにする必要が生じる場合があります。  この方法の 1 つに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリを作成し、そのアセンブリを COM を使用して登録して GAC にインストールし、Visual Basic コードで COM 型を参照する方法があります。  アプリケーションを配布するときに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリも配信する必要があります。  次にユーザーは COM を使用して WCF クライアント アセンブリを登録し、それを GAC に配置する必要があります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] COM Interop でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリに依存しない同じサービス呼び出しを作成できます。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] モニカーを使用すれば、サービスに関する型情報を抽出するためにサービス モニカーで使用されるメタデータ交換 \(Mex\) エンドポイント URI を指定することにより、必要な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを任意の COM 互換言語 \(Visual Basic、VBScript、Visual Basic for Applications \(VBA\) など\) から呼び出すことができます。  ここでは、Mex エンドポイントを指定する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] モニカーを使用して、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の入門サンプルを呼び出す方法を説明します。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリで定義された型は、実際にインスタンス化されることはありません。  アセンブリはメタデータにのみ使用されます。  
  
### Mex アドレスを使うサービス モニカーの使用  
  
1.  入門サンプルを構築し、Internet Explorer を使用してその URL \(http:\/\/localhost\/ServiceModelSamples\/Service.svc\) を参照し、サービスが動作していることを確認します。  
  
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
    >  モニカーがサービスのメタデータを読み取るには、呼び出すサービスで、Mex エンドポイントが公開されている必要があります。  詳細については、「[方法 : 構成ファイルを使用してサービスのメタデータを公開する](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)」を参照してください。  
  
    > [!NOTE]
    >  モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。  
  
## 参照  
 [方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)   
 [方法 : WSDL コントラクトと共にサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)