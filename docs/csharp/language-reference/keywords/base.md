---
title: base (C# リファレンス)
description: C# で派生クラス内から基底クラスのメンバーにアクセスするために使用する base キーワードについて説明します。
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1bbaa0cc05b35f822113bc3a8c3cde966b1484ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="base-c-reference"></a>base (C# リファレンス)

`base` キーワードは、派生クラス内から基底クラスのメンバーにアクセスするために使います。

- 別のメソッドによってオーバーライドされた基底クラスのメソッドを呼び出します。

- 派生クラスのインスタンスを作成するときに基底クラスのどのコンストラクターを呼び出す必要があるかを指定します。

基底クラスへのアクセスは、コンストラクター、インスタンス メソッド、またはインスタンスのプロパティ アクセサーにおいてのみ許可されます。

静的メソッド内から `base` キーワードを使うとエラーになります。

アクセスされる基底クラスは、クラス宣言で指定されている基底クラスです。 たとえば、`class ClassB : ClassA` と指定すると、ClassA の基底クラスに関係なく、ClassA のメンバーが ClassB からアクセスされます。

## <a name="example"></a>例
この例では、基底クラス `Person` と派生クラス `Employee` の両方に、`Getinfo` という名前のメソッドがあります。 `base` キーワードを使うことで、派生クラス内から基底クラスの `Getinfo` メソッドを呼び出すことができます。

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

その他の例については、「[new](../../../csharp/language-reference/keywords/new.md)」、「[virtual](../../../csharp/language-reference/keywords/virtual.md)」、「[override](../../../csharp/language-reference/keywords/override.md)」をご覧ください。

## <a name="example"></a>例
この例では、派生クラスのインスタンスを作成するときに呼び出される基底クラスのコンストラクターを指定する方法を示します。

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>C# 言語仕様
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [this](../../../csharp/language-reference/keywords/this.md)