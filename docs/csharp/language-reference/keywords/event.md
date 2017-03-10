---
title: "event (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "event"
  - "remove"
  - "event_CSharpKeyword"
  - "add"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "event キーワード [C#]"
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# event (C# リファレンス)
`event` キーワードを使用して、パブリッシャー クラス内にイベントを宣言します。  
  
## 使用例  
 次の例では、基になるデリゲート型として <xref:System.EventHandler> を使用するイベントを宣言し、発生させる方法について説明します。  完全なコード例については、「[方法 : .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)」を参照してください。完全なコード例では、ジェネリック <xref:System.EventHandler%601> デリゲート型の使用方法、イベント サブスクリプションの実行方法、およびイベント ハンドラー メソッドの作成方法も確認できます。  
  
 [!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#7)]  
  
 イベントは、宣言元 \(パブリッシャー クラス\) のクラスまたは構造体内でしか呼び出せない特殊なマルチキャスト デリゲートです。  その他のクラスまたは構造体のイベントをサブスクライブすると、パブリッシャー クラスがイベントを発生させるときにイベント ハンドラー メソッドが呼び出されます。  詳細およびコード例については、「[イベント](../../../csharp/programming-guide/events/index.md)」および「[デリゲート](../../../csharp/programming-guide/delegates/index.md)」を参照してください。  
  
 イベントは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected` `internal` とマークできます。  これらのアクセス修飾子により、クラスのユーザーがイベントにどのようにアクセスできるかが定義されます。  詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
## キーワードとイベント  
 イベントには次のキーワードが適用されます。  
  
|Keyword|Description|詳細情報|  
|-------------|-----------------|----------|  
|[static](../../../csharp/language-reference/keywords/static.md)|このように宣言すると、クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもイベントを使用できるようになります。|[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|この場合、派生クラスでは、[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用して、イベントの動作をオーバーライドできます。|[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|派生クラスが virtual でなくなったことを示します。||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|コンパイラはイベント アクセサー ブロック `add` および `remove` を生成しません。したがって、派生クラスは固有の実装を提供する必要があります。||  
  
 イベントは、[static](../../../csharp/language-reference/keywords/static.md) キーワードを使用して静的イベントと宣言することもできます。  このように宣言すると、クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもイベントを使用できるようになります。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 また、イベントは、[virtual](../../../csharp/language-reference/keywords/virtual.md) キーワードを使用して仮想イベントとマークできます。  この場合、派生クラスでは、[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用して、イベントの動作をオーバーライドできます。  詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  仮想イベントをオーバーライドするイベントは、[sealed](../../../csharp/language-reference/keywords/sealed.md) にすることもできます。この場合、派生クラスでは、イベントが仮想でなくなります。  最後に、イベントは [abstract](../../../csharp/language-reference/keywords/abstract.md) としても宣言できます。この場合、コンパイラはイベント アクセサー ブロック `add` および `remove` を生成しません。  したがって、各派生クラスで固有の実装を提供する必要があります。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [add](../../../csharp/language-reference/keywords/add.md)   
 [remove](../../../csharp/language-reference/keywords/remove.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [方法 : デリゲートを結合する \(マルチキャスト デリゲート\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)