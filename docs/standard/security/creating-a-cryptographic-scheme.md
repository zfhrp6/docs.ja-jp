---
title: "暗号スキームの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "暗号化 [.NET Framework], 作成 (暗号化スキームを)"
  - "暗号化 [.NET Framework], 作成 (暗号化スキームを)"
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 暗号スキームの作成
.NET Framework の暗号化コンポーネントを組み合わせて、データの暗号化と復号化を行うさまざまなスキームを作成することができます。  
  
 データの暗号化と復号化の単純な暗号スキームでは、次の手順を指定することがあります。  
  
1.  暗号化側と復号化側は、公開キーと秘密キーのペアを生成する。  
  
2.  暗号化側と復号化側は、公開キーを交換する。  
  
3.  暗号化側と復号化側は、たとえば TripleDES 暗号化の秘密キーを生成する。続いて、相手側の公開キーを使用して新規作成されたキーを暗号化する。  
  
4.  暗号化側と復号化側は、相手側にデータを送信し、特定の順序で相手側の秘密キーを自分の秘密キーと組み合わせて、新しい秘密キーを作成する。  
  
5.  暗号化側と復号化側は、対称暗号化を使って会話を開始する。  
  
 暗号スキームの作成は簡単な作業ではありません。  暗号化の使用の詳細については、http:\/\/msdn.microsoft.com\/library のプラットフォーム SDK ドキュメントにある「暗号化」トピックを参照してください。  
  
## 参照  
 [暗号サービス](../../../docs/standard/security/cryptographic-services.md)