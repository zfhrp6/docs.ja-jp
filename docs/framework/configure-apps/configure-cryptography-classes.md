---
title: "暗号化クラスの設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework アプリケーション構成, 暗号化"
  - "構成ファイル [.NET Framework], 暗号化"
  - "暗号アルゴリズム"
  - "暗号化, クラス"
  - "既定の暗号化"
  - "セキュリティ [.NET Framework], 暗号化"
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 暗号化クラスの設定
コンピューターの管理者は、[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] を使用して、.NET Framework および正しく作成されたアプリケーションが使用する既定の暗号化アルゴリズムおよびアルゴリズム実装を設定できます。たとえば、独自の暗号化アルゴリズム実装を持つエンタープライズは、その実装を、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)] に付属する実装の代わりに既定の実装として使用できます。  暗号を使用するマネージ アプリケーションは常に特定の暗号化アルゴリズム実装をバインドするように選択できますが、暗号構成システムを使用して暗号オブジェクトを作成することをお勧めします。  
  
## このセクションの内容  
 [暗号化クラスへのアルゴリズム名の割り当て](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 暗号化クラスにアルゴリズム名を割り当てる方法を説明します。  
  
 [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 暗号化アルゴリズムにオブジェクト ID を割り当てる方法を説明します。  
  
## 関連項目  
 [暗号サービス](../../../docs/standard/security/cryptographic-services.md)  
 [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)] によって提供される暗号サービスの概要を説明します。  
  
 [暗号設定スキーマ](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。