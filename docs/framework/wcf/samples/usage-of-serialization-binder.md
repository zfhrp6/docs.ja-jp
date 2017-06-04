---
title: "シリアル化バインダーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# シリアル化バインダーの使用
このサンプルでは、<xref:System.Runtime.Serialization.SerializationBinder> を使用して、ジェネリック型のバージョンをシリアル化する際に変更する方法を示します。  
  
## 使用例  
 <xref:System.Runtime.Serialization.SerializationBinder>,<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## 説明  
 このサンプルでは、さまざまなバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] を対象とする 2 つのエンティティで、バイナリ フォーマッタとシリアル化バインダーを使用して通信する方法を示します。  
  
 このサンプルの開発は、.NET リモート処理を使用して行われました。このサンプルは、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] を対象とするサーバー \(ジェネリック型を含むコントラクトを実装しています\) と、2 つの異なるクライアント \(1 つは [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] を対象とし、もう 1 つは [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] を対象としています\) で構成されています。  
  
 このサーバーは、シリアル化の際に型のバージョンを相応に変更できるようにするために、<xref:System.Runtime.Serialization.SerializationBinder> をバイナリ フォーマッタにアタッチします。これにより、両方のクライアントで、これらの型を適切に逆シリアル化できるようになります。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  クライアントを実行するには、SBGenericsVTS ソリューション \(6 つのプロジェクト\) を右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[共通プロパティ\]** で、**\[スタートアップ プロジェクト\]** をクリックし、**\[マルチ スタートアップ プロジェクト\]** をクリックします。  
  
3.  **\[Server\]**、**\[Client20\]**、**\[Client40\]** の順に選択します。これら 3 つのプロジェクトのアクションとして **\[開始\]** を選択し、その他のプロジェクトの設定は **\[なし\]** のままにしておきます。  
  
4.  **\[OK\]** をクリックし、F5 キーを押してサンプルを実行します。