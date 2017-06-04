---
title: "方法: クライアント データ サービス クラスを手動で生成する (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, クライアント ライブラリ"
  - "WCF Data Services, 構成"
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法: クライアント データ サービス クラスを手動で生成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を Visual Studio に統合すると、**\[サービス参照の追加\]** ダイアログ ボックスを使用して参照を Visual Studio プロジェクト内のデータ サービスに追加するときに、クライアント データ サービス クラスを自動的に生成できるようになります。  詳細については、「[方法: データ サービス参照を追加する](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)」を参照してください。  コード生成ツールの `DataSvcUtil.exe` を使用して、同じクライアント データ サービス クラスを手動で生成することもできます。[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] に含まれるこのツールは、データ サービス定義から .NET Framework クラスを生成します。  このツールを使用して、概念モデル \(.csdl\) ファイル、および Visual Studio プロジェクトの Entity Framework モデルを表す .edmx ファイルからデータ サービス クラスを生成することもできます。  
  
 このトピックの例は、Northwind サンプル データ サービスに基づいてクライアント データ サービス クラスを作成します。  このサービスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  このトピックのいくつかの例では、Northwind モデルの概念モデル ファイルが必要です。  詳細については、「[方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)」を参照してください。  このトピックのいくつかの例では、Northwind モデルの .edmx ファイルが必要です。  詳細については、「[.edmx File Overview](http://msdn.microsoft.com/ja-jp/f4c8e7ce-1db6-417e-9759-15f8b55155d4)」を参照してください。  
  
### データ バインディングをサポートする C\# クラスを生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。  
  
### データ バインディングをサポートする Visual Basic クラスを生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。  
  
### サービス URI に基づいて C\# クラスを生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。  
  
### サービス URI に基づいて Visual Basic クラスを生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  `/uri:` パラメーターの値は Northwind サンプル データ サービスのインスタンスの URI で置き換える必要があります。  
  
### 概念モデル ファイル \(CSDL\) に基づいて C\# を生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### 概念モデル ファイル \(CSDL\) に基づいて Visual Basic を生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### .edmx ファイルに基づいて C\# クラスを生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### .edmx ファイルに基づいて Visual Basic クラスを生成するには  
  
-   コマンド プロンプトで、次のコマンド \(改行なし\) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## 参照  
 [データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)   
 [方法: データ サービス参照を追加する](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)   
 [WCF Data Service クライアント ユーティリティ \(DataSvcUtil.exe\)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)