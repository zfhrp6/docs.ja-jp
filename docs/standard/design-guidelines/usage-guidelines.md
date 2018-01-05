---
title: "使用方法のガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3f0a38c69dc286587e702b80ef4093bb98d78b5a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="usage-guidelines"></a>使用方法のガイドライン
このセクションには、パブリックにアクセスできる Api の一般的な種類の使用に関するガイドラインが含まれています。 組み込みフレームワーク型 (シリアル化属性など) および一般的な演算子をオーバー ロードの直接の使用状況を処理します。  
  
 <xref:System.IDisposable?displayProperty=nameWithType>インターフェイスは、このセクションでは説明しませんが、については、 [Dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)セクションです。  
  
> [!NOTE]
>  ガイドラインとその他の一般的なに関する追加情報、組み込みの .NET Framework 型を参照してください、次の参照トピック: <xref:System.DateTime?displayProperty=nameWithType>、 <xref:System.DateTimeOffset?displayProperty=nameWithType>、 <xref:System.ICloneable?displayProperty=nameWithType>、 <xref:System.IComparable%601?displayProperty=nameWithType>、 <xref:System.IEquatable%601?displayProperty=nameWithType>、 <xref:System.Nullable%601?displayProperty=nameWithType>、 <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.  
  
## <a name="in-this-section"></a>このセクションの内容  
 [配列](../../../docs/standard/design-guidelines/arrays.md)  
 [属性](../../../docs/standard/design-guidelines/attributes.md)  
 [コレクション](/cpp/mfc/collections)  
 [シリアル化](../../../docs/standard/design-guidelines/serialization.md)  
 [System.Xml の使用法](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [等値演算子](../../../docs/standard/design-guidelines/equality-operators.md)  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
