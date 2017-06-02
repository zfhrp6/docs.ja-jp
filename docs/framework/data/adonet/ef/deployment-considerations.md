---
title: "配置に関する注意事項 (Entity Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 配置に関する注意事項 (Entity Framework)
このトピックでは、データ アクセスに ADO.NET Entity Framework を使用するアプリケーションの配置について説明します。  Entity Framework の詳細については、「[はじめに](../../../../../docs/framework/data/adonet/ef/getting-started.md)」を参照してください。  
  
 Entity Framework は、Visual Studio に組み込むことにより Visual Studio での開発を容易にする一連のツールを提供します。  詳細については、「[ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527)」を参照してください。  このトピックでは、Entity Framework ベースのアプリケーションを配置するための具体的なテクノロジの使用法については触れません。  
  
 Visual Studio では、ClickOnce 配置など、アプリケーションの配布および配置のための機能が提供されています。  詳細については、Visual Studio ドキュメントの「[アプリケーションとコンポーネントの配置](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)」を参照してください。  
  
 Entity Framework を使用するアプリケーションを配置する場合は、次の注意事項が適用されます。  
  
-   .NET Framework 3.5 Service Pack 1 \(SP1\) 以降、Entity Framework は .NET Framework のコンポーネントになっています。  Entity Framework ベースのアプリケーションを配置する場合は、.NET Framework 3.5 SP1 以降のバージョンがインストールされていることを確認する必要があります。  
  
-   Entity Data Model ウィザードで概念モデルが生成されると、アプリケーション設定ファイルに接続文字列が作成されます。  モデル ファイルおよびマッピング ファイルをアプリケーション リソースとして埋め込むか、出力ディレクトリにコピーすることができます。  既定では、モデル ファイルとマッピング ファイルは、組み込みアプリケーション リソースとして配置されます。  エンティティ デザイナー ファイルの `Metadata Artifact Processing` プロパティを使用して、次のオプションのいずれかを選択することができます。  詳細については、「[How to: Copy Model and Mapping Files to the Output Directory](http://msdn.microsoft.com/ja-jp/e2c9820f-1705-457e-9fdb-8b289f3179b4)」を参照してください。  
  
-   モデルとマッピングの情報 \(概念スキーマ定義言語 \(CSDL\)、ストア スキーマ定義言語 \(SSDL\)、およびマッピング仕様言語 \(MSL\) で表現\) は、アプリケーションと共に配置され、その場所は、接続文字列によって指定されます。  詳細については、「[接続文字列](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」を参照してください。  
  
-   モデルとマッピングの情報をアプリケーション リソースとして組み込む場合は、概念モデルを更新するたびに、アプリケーションの再コンパイルと再配置が必要になります。  
  
-   Entity Framework は .NET Framework のコンポーネントであるため、.NET Framework 使用許諾契約書での許可に従ってアプリケーションと共に再配布できます。  
  
## 参照  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)   
 [開発および配置に関する注意事項](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)