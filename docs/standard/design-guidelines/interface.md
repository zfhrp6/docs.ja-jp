---
title: インターフェイスのデザイン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc7185f9541952d528de38b627052239f5d8b4ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="interface-design"></a>インターフェイスのデザイン
ほとんどの Api は、クラスと構造体を使用して、最適なモデル化、ある場合、またはインターフェイスがより適切な唯一のオプションします。  
  
 CLR は多重継承をサポートしていません (つまり、CLR クラスは継承できません 1 つ以上の基底クラスから) が、基本クラスから継承するだけでなく、1 つまたは複数のインターフェイスを実装する型。 そのため、インターフェイスは、複数の継承の効果を実現するためによく使用されます。 たとえば、<xref:System.IDisposable>インターフェイスにより、参加する継承階層の独立した disposability をサポートする型です。  
  
 どのを定義するインターフェイスが適切な他の状況は、いくつかの値の型を含む、いくつかの種類でサポートできる共通のインターフェイスを作成するのにです。 値の型が以外の値の型から継承できません<xref:System.ValueType>インターフェイスを実装することができますが、共通の基本型を提供するための唯一のオプションは、インターフェイスを使用します。  
  
 **✓ しないで**いくつかの一般的な API 値の型を含む型のセットでサポートする必要がある場合は、インターフェイスを定義します。  
  
 **✓ を検討してください**既に他の型を継承する型でその機能をサポートする必要がある場合は、インターフェイスを定義します。  
  
 **避け x**マーカー インターフェイス (メンバーを持たないインターフェイス) を使用します。  
  
 特定の特性 (マーカー) を持つものとしてクラスをマークする必要がある場合は、一般に、インターフェイスではなく、カスタム属性を使用します。  
  
 **✓ しないで**インターフェイスの実装は、少なくとも 1 つの型を提供します。  
  
 これにより、インターフェイスの設計を検証するを行っています。 たとえば、<xref:System.Collections.Generic.List%601>に実装されて、<xref:System.Collections.Generic.IList%601>インターフェイスです。  
  
 **✓ しないで**を定義する各インターフェイスを使用するには、少なくとも 1 つの API を提供 (パラメーターまたはプロパティとして、インターフェイス メソッドは、インターフェイスとして型指定された)。  
  
 インターフェイスの設計を検証するには、これによりを行っています。 たとえば、<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>消費、<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>インターフェイスです。  
  
 **X しないで**以前に出荷されたインターフェイスにメンバーを追加します。  
  
 これにより、インターフェイスの実装の使用できなくなります。 バージョン管理の問題を回避するために、新しいインターフェイスを作成する必要があります。  
  
 を除き、これらのガイドライン」に説明されている場合、マネージ コードの再利用可能なライブラリをデザイン インターフェイスではなく、クラスを選択してください、一般に。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
