---
title: "暗号化クラスの設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 23bd6007beb870895316a565283ee7e7354c931b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-cryptography-classes"></a>暗号化クラスの設定
[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]により、既定の暗号化アルゴリズムと .NET Framework および適切に記述されたアプリケーションを使用するアルゴリズムの実装を構成するコンピューターの管理者です。  たとえば、暗号アルゴリズムの実装を持つエンタープライズは、その実装に付属して実装ではなく既定値、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]です。 暗号化を使用するマネージ アプリケーションは、特定の実装にバインドするように常に選択できますが、暗号化の構成システムを使用して暗号オブジェクトを作成することをお勧めします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [暗号化クラスへのアルゴリズム名の割り当て](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 アルゴリズム名を暗号クラスにマップする方法について説明します。  
  
 [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 暗号化アルゴリズムにオブジェクト識別子をマップする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
 によって提供される暗号サービスの概要を示します、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]です。  
  
 [暗号化設定スキーマ](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。
