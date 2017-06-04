---
title: "例外とパフォーマンス | Microsoft Docs"
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
  - "tester-doer パターン"
  - "TryParse パターン"
  - "例外のスロー"
  - "パフォーマンスの例外"
  - "パフォーマンスの例外をスロー"
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 例外とパフォーマンス
例外に関連する一般的な懸念事項の 1 つは、定期的に失敗するコードの例外を使用している場合、実装のパフォーマンスがされる許容です。 これはもっともです。 メンバーは、例外をスローするときに、パフォーマンスが極端に遅くにできます。 ただし、エラー コードの使用を許可しない例外のガイドラインに厳密に準拠しつつ、良好なパフォーマンスを実現することができます。 このセクションで説明した 2 つのパターンでは、これを行う方法を提案します。  
  
 **X のしないで** エラー コードを使用して、例外がパフォーマンスに悪影響を及ぼす影響する問題があるためです。  
  
 パフォーマンスを向上させる Tester\-doer パターンまたは Try 解析パターンは、次の 2 つのセクションで説明されているのいずれかを使用することができます。  
  
## Tester\-doer パターン  
 場合があります、メンバーを 2 つに分割することにより、例外のスローを持つメンバーのパフォーマンスを向上することができます。 見て、 <xref:System.Collections.Generic.ICollection%601.Add%2A> のメソッド、 <xref:System.Collections.Generic.ICollection%601> インターフェイスです。  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 メソッド `Add` コレクションは読み取り専用の場合にスローします。 これは、メソッドの呼び出しが多くの場合、失敗を想定している場所のシナリオでパフォーマンス問題であることができます。 問題を緩和する方法の 1 つは、値を追加する前に、コレクションが書き込み可能かどうかをテストします。  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 プロパティであるこの例では、条件をテストに使用するメンバー `IsReadOnly`, 、テスト担当者と呼びます。 スロー元可能性のある操作を実行するために使用するメンバー、 `Add` 例では、メソッドは、渡ってと呼ばれます。  
  
 **✓ を検討してください** Tester\-doer パターンに例外をスローするメンバーの共通のシナリオのパフォーマンスの問題を回避する例外に関連します。  
  
## Try 解析パターン  
 非常に高く、パフォーマンスが重視される Api では、前のセクションで説明した Tester\-doer パターンよりもさらに高速のパターンを使用してください。 メンバーのセマンティクスの一部の場合、適切に定義されたテストを作成するメンバーの名前を調整するためのパターンを呼び出します。 たとえば、 <xref:System.DateTime> を定義、 <xref:System.DateTime.Parse%2A> 文字列の解析に失敗した場合に例外をスローするメソッドです。 対応するも定義されて <xref:System.DateTime.TryParse%2A> を解析しようとするには false が返されます解析は失敗し、正常に解析を使用して、結果を返す場合、 `out` パラメーター。  
  
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
  
 このパターンを使用する場合は、厳密な用語で try 機能を定義する必要があります。 メンバーは、適切に定義された try 以外の何らかの理由で失敗した場合、メンバーが対応する例外をスローする必要があります。  
  
 **✓ を検討してください** Try 解析パターンに例外をスローするメンバーの共通のシナリオのパフォーマンスの問題を回避する例外に関連します。  
  
 **✓ は** このパターンを実装するメソッドにプレフィックス"Try"とブール値の戻り値の型を使用します。  
  
 **✓ は** Try 解析パターンを使用する各メンバーの例外のスローを持つメンバーを提供します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)