---
title: 構造体のデザイン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f4a6debc25a51e3a0a83e70fc8c8f8fc55c62f5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="struct-design"></a>構造体のデザイン
ほとんどの場合に、汎用的な値の型を構造体、その c# キーワードと呼びます。 このセクションでは、一般的な構造体のデザインのガイドラインを示します。  
  
 **X しないで**構造体の既定のコンス トラクターを提供します。  
  
 このガイドラインに従う、配列の各項目で、コンス トラクターを実行しなくても作成する構造体の配列を使用できます。 C# は許可されていないことを既定のコンス トラクターを持つ構造体に注意してください。  
  
 **X しないで**変更可能な値の型を定義します。  
  
 変更可能な値の型には、いくつかの問題があります。 たとえば、プロパティ get アクセス操作子が値型を返すときに、呼び出し元は、コピーを受け取ります。 コピーが暗黙的に作成されるため、開発者が、コピー、および元の値ではなくを変更することに注意してくださいできない可能性があります。 また、一部の言語 (動的言語、特に) では、逆参照時に、ローカル変数があっても、コピーできるようにするために、変更可能な値の型を使用して問題があります。  
  
 **✓ しないで**すべてのインスタンス データの状態が 0 に設定されている、false の場合、または null (該当する場合) が有効であることを確認します。  
  
 構造体の配列の作成時に、無効なインスタンスの偶発的な作成ができなくなります。  
  
 **✓ は**実装<xref:System.IEquatable%601>を値の型。  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>メソッド値の型をボックス化、発生して、既定の実装はリフレクションを使用しているため、非常に効率はします。 <xref:System.IEquatable%601.Equals%2A>多くのパフォーマンスが向上し、ボックス化は発生しませんできるように実装することができます。  
  
 **X しないで**明示的に拡張<xref:System.ValueType>です。 実際には、ほとんどの言語は、これを防ぐ。  
  
 一般に、構造体は、非常に役に立ちますが、いないボックス化頻繁に小さく、1 つ、変更できない値に対してのみ使用する必要があります。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [クラスまたは構造体の選択](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
