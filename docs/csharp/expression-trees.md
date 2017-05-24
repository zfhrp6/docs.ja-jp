---
title: Expression Trees
description: Expression Trees
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e6ec60b6cdbe29def719f7970dad15fad65902e7
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---

# <a name="expression-trees"></a>Expression Trees

LINQ を使ったことがあれば、API セットに `Func` 型が含まれる豊富なライブラリを利用したのではないでしょうか (LINQ の知識があまりない場合は、この記事の前に、[LINQ のチュートリアル](linq/index.md)と[ラムダ式](lambda-expressions.md)のチュートリアルを読むことをお勧めします)。*式ツリー*には、関数である引数とのさまざまな相互作用があります。

LINQ クエリを作成するときに関数の引数を作成するには、通常、ラムダ式を使用します。 一般的な LINQ クエリでは、このような関数の引数は、コンパイラで作成されるデリゲートに変換されます。 

さまざまな相互作用を使用するには、*式ツリー*を使用する必要があります。
式ツリーは、確認、変更、または実行が可能な構造としてコードを表します。 このようなツールを使用すると、実行時にコードを操作できるようになります。 実行中のアルゴリズムを確認するコードや、新しい機能を挿入するコードを作成できます。 より高度なシナリオの場合、実行中のアルゴリズムを変更し、別の環境で実行できるように C# 式を別の形式に変換することもできます。

式ツリーを使用するコードは既に作成してきました。 Entity Framework の LINQ API では、LINQ クエリ式パターンの引数として式ツリーを使用できます。
そのため、[Entity Framework](http://docs.efproject.net/en/latest/) では、C# で作成したクエリをデータベース エンジンで実行される SQL に変換することができます。 もう 1 つの例として [Moq](https://github.com/Moq/moq) があります。Moq は、.NET でよく使われるモック作成フレームワークです。

以降、このチュートリアルでは、式ツリーの概要、式ツリーをサポートするフレームワーク クラス、式ツリーの使用方法について説明します。 式ツリーの読み方、式ツリーの作成方法、変更を加えた式ツリーの作成方法、式ツリーで表されるコードの実行方法を学びます。 チュートリアルを読み終わると、これらの構造を使用し、高度な適合アルゴリズムを作成できるようになります。
<style type="text/css"> ol { list-style-type: upper-roman; } </style>
1. [式ツリーの説明](expression-trees-explained.md)

    Understand the structure and concepts behind *Expression Trees*.
    
2. [式ツリーをサポートするフレームワークの型](expression-classes.md)
    
    式ツリーを定義し、操作する構造とクラスについて説明します。
    
3. [式の実行](expression-trees-execution.md)

    ラムダ式で表される式ツリーをデリゲートに変換し、結果のデリゲートを実行する方法について説明します。

4. [式の解釈](expression-trees-interpreting.md)

    式ツリーを走査して確認し、*式ツリー*が表すコードの内容を理解する方法について説明します。

5. [式の構築](expression-trees-building.md)

    式ツリーのノードを構築し、式ツリーを構築する方法について説明します。

6. [式の変換](expression-trees-translating.md)

    式ツリーに変更を加えたコピーを構築する方法、または式ツリーを別の形式に変換する方法について説明します。

7. [まとめ](expression-trees-summary.md)

    式ツリーに関する情報のまとめです。
    

