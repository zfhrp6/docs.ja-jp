---
title: "拡張メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7edc3420eabe4de20a2fe39f38ae5eee53b593c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods"></a>拡張メソッド
拡張メソッドは、言語の機能により、インスタンス メソッドの呼び出し構文を使用して呼び出されるメソッドは静的です。 これらのメソッドは、操作するためには、メソッドのインスタンスを表すには、少なくとも 1 つのパラメーターを取得する必要があります。  
  
 このような拡張メソッドを定義するクラスが「スポンサー」クラスと呼ばれ、静的な宣言する必要があります。 拡張メソッドを使用するには、スポンサー クラスを定義する名前空間をインポートいずれかの必要があります。  
  
 **避け x**いないこと、お持ちでない型に特に拡張メソッドを定義します。  
  
 型のソース コードを所有する場合は、通常のインスタンス メソッドを代わりに使用することを検討します。 所有していない場合に、メソッドを追加するには、十分に注意します。 拡張メソッドを多めに使用では、これらのメソッドがあるように設計されていない種類の Api に混乱が生じる可能性があります。  
  
 **✓ を検討してください**拡張メソッドを使用して、次のシナリオのいずれかで。  
  
-   ヘルパーを提供するには、コア インターフェイスの観点から機能と言われます場合、インターフェイスのすべての実装に関連する機能を記述できます。 具体的な実装は、インターフェイスそれ以外の場合に割り当てることができないためにです。 たとえば、`LINQ to Objects`演算子がすべての拡張メソッドとして実装されて<xref:System.Collections.Generic.IEnumerable%601>型です。 したがって、いずれか`IEnumerable<>`実装が自動的に LINQ 有効にします。  
  
-   インスタンス メソッドがいくつかの型への依存関係が、このような依存関係をどのように発生する場合、依存関係の管理規則ができなくなります。 依存関係など、<xref:System.String>に<xref:System.Uri?displayProperty=nameWithType>が許容されない可能性がありますので`String.ToUri()`を返すインスタンス メソッド`System.Uri`依存関係の管理の観点から正しくないデザインになります。 拡張機能の静的メソッド`Uri.ToUri(this string str)`返す`System.Uri`量より優れた設計になります。  
  
 **避け x**で拡張メソッドを定義する<xref:System.Object?displayProperty=nameWithType>です。  
  
 VB のユーザーは拡張メソッド構文を使用してオブジェクト参照でこのようなメソッドを呼び出すことができません。 VB は vb の場合は参照を宣言するオブジェクトが遅延するすべてのメソッド呼び出しを強制的にバインドされているため、このようなメソッドの呼び出しをサポートしていません (と呼ばれる実際のメンバーは実行時に決定されます) 中、拡張メソッドへのバインドはコンパイル時 (早期に決定されますバインドされている)。  
  
 ガイドラインは、同じバインド動作が存在するその他の言語に適用されることに注意してください。 または、拡張メソッドはサポートされていません。  
  
 **X しないで**インターフェイスにメソッドを追加または依存関係の管理用である場合を除き、拡張の型と同じ名前空間の拡張メソッドを格納します。  
  
 **避け x**異なる名前空間にある場合でも、同じシグネチャを持つ 2 つ以上の拡張メソッドを定義します。  
  
 **✓ を検討してください**型がインターフェイスで、ほとんどまたはすべてのケースで使用する拡張メソッドは、拡張された型と同じ名前空間に拡張メソッドを定義します。  
  
 **X しないで**通常その他の機能に関連付けられている名前空間の機能を実装する拡張メソッドを定義します。 代わりに、所属する機能に関連付けられている名前空間で定義します。  
  
 **避け x**拡張メソッド (たとえば、「拡張」) を専用の名前空間の汎用名前付けします。 わかりやすい名前 (たとえば、「ルーティング」) 代わりにします。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [メンバーのデザイン ガイドライン](../../../docs/standard/design-guidelines/member.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
