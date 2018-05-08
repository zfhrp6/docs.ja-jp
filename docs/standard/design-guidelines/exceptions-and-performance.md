---
title: 例外とパフォーマンス
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfffc2a1c0f607541194a7f51717d5bf8a8537f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-and-performance"></a>例外とパフォーマンス
例外に関連する 1 つの一般的な問題は、こと日常的に失敗したコードの例外を使用する場合の実装では、パフォーマンスは許容できないです。 これは、有効な問題です。 メンバーは、例外をスローするときに、パフォーマンスが桁違い低速にできます。 ただし、厳密にエラー コードの使用を許可しない例外のガイドラインに従いながら良好なパフォーマンスを実現することはできます。 このセクションで説明した 2 つのパターンは、これを行う方法を提案します。  
  
 **X しないで**例外がパフォーマンスに悪影響を及ぼす影響する問題が原因のエラー コードを使用します。  
  
 パフォーマンスを向上させるには、可能であれば、テスター渡ってパターンまたは Try 解析パターンは、次の 2 つのセクションで説明を使用します。  
  
## <a name="tester-doer-pattern"></a>テスト担当者渡ってパターン  
 場合があります、メンバーを 2 つに分割することにより例外スロー メンバーのパフォーマンスを向上することができます。 見てみましょう、<xref:System.Collections.Generic.ICollection%601.Add%2A>のメソッド、<xref:System.Collections.Generic.ICollection%601>インターフェイスです。  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 メソッド`Add`コレクションが読み取り専用である場合にスローされます。 メソッドの呼び出しが多くの場合、失敗すると思われるシナリオでパフォーマンスの問題を指定できます。 値を追加する前に、コレクションが書き込み可能かどうかをテストすると、問題を軽減する方法のいずれかです。  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 状態は、この例では、プロパティをテストに使用するメンバー`IsReadOnly`は、テスト担当者と呼びます。 可能性のあるスロー元の操作の実行に使用されるメンバー、`Add`例では、メソッドは、渡ってと呼ばれます。  
  
 **✓ を検討してください**Tester 渡ってパターンが例外をスローするメンバーの共通のパフォーマンスの問題を回避するシナリオに関連する例外。  
  
## <a name="try-parse-pattern"></a>Try 解析パターン  
 非常にパフォーマンスが重視される Api では、前のセクションで説明されているテスト担当者渡ってパターンよりも高速のパターンを使用してください。 メンバーのセマンティクスの一部の場合、適切に定義されたテストを作成するメンバーの名前を調整するため、パターンを呼び出します。 たとえば、<xref:System.DateTime>定義、<xref:System.DateTime.Parse%2A>文字列の解析に失敗した場合に例外をスローするメソッド。 対応する定義も<xref:System.DateTime.TryParse%2A>を解析しようとするメソッドが false を返します解析が失敗し、正常に解析を使用して、結果を返す場合、`out`パラメーター。  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 このパターンを使用する場合は、厳密な用語で try 機能を定義する必要があります。 メンバーは、適切に定義された再試行以外の何らかの理由で失敗した場合、メンバーが対応する例外をスローする必要があります。  
  
 **✓ を検討してください**Try 解析パターンが例外をスローするメンバーの共通のパフォーマンスの問題を回避するシナリオに関連する例外。  
  
 **✓ しないで**このパターンを実装するメソッドにプレフィックス"Try"とブール型の戻り値の型を使用します。  
  
 **✓ しないで**Try 解析パターンを使用する各メンバーに対して例外スローのメンバーを提供します。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
