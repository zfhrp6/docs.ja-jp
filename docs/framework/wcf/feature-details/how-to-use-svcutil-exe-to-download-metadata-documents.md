---
title: "方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 102b605b0b985d433092482cf55b0994c33d58ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>方法 : Svcutil.exe を使用してメタデータ ドキュメントをダウンロードする
Svcutil.exe を使用すると、実行中のサービスからメタデータをダウンロードして、ローカル ファイルに保存できます。 HTTP および HTTPS の URL スキームの場合、Svcutil.exe は Ws-metadataexchange を使用してメタデータの取得を試みますと[XML Web サービス探索](http://go.microsoft.com/fwlink/?LinkId=94950)です。 その他の URL スキームの場合、Svcutil.exe は WS-MetadataExchange のみを使用します。  
  
 既定で、Svcutil.exe は <xref:System.ServiceModel.Description.MetadataExchangeBindings> クラスに定義されているバインディングを使用します。 WS-MetadataExchange で使用するバインディングを構成するには、Svcutil.exe の構成ファイル (svcutil.exe.config) でクライアント エンドポイントを定義する必要があります。このとき、クライアント エンドポイントが `IMetadataExchange` コントラクトを使用し、メタデータ エンドポイントのアドレスの URI (Uniform Resource Identifier) スキームと同じ名前を持つように定義します。  
  
> [!CAUTION]
>  2 つの異なるサービスを公開するサービスのメタデータを取得する Svcutil.exe を実行しているコントラクトの同じ名前の操作が含まれていることと、Svcutil.exe では"できませんからメタデータを取得しています..."というメッセージが、エラーが表示されます。たとえばと呼ばれるサービス コントラクトを公開するサービスを使用していれば、操作を含む ICarService Get (Car c) と、同じサービスが ibookservice という get (Book b) サービス コントラクトを公開します。 この問題を回避するには、次のいずれかの操作を実行します。  
>   
>  -   操作の名前を変更する。  
> -   <xref:System.ServiceModel.OperationContractAttribute.Name%2A> を別の名前に設定する。  
> -   <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティを使用して、操作の名前空間のいずれかを別の名前空間に設定する。  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Svcutil.exe を使用してメタデータをダウンロードするには  
  
1.  次の場所で Svcutil.exe ツールを検索します。  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  コマンド プロンプトで、次の形式を使用してツールを起動します。  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     メタデータをダウンロードするには `/t:metadata` オプションを指定する必要があります。 このオプションを指定しないと、クライアントのコードと構成が生成されます。  
  
3.  <`url`> 引数は、メタデータを提供するサービス エンドポイントまたはオンラインになっているメタデータ ドキュメントの URL を指定します。 <`epr`> 引数を WS アドレス指定を含む XML ファイルへのパスを指定する`EndpointAddress`Ws-metadataexchange をサポートするサービス エンドポイントにします。  
  
 メタデータのダウンロード用にこのツールを使用する方法の詳細については、次を参照してください。 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。  
  
## <a name="example"></a>例  
 次のコマンドにより、実行中のサービスからメタデータ ドキュメントがダウンロードされます。  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>関連項目  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
