---
title: "式ツリーのまとめ"
description: "式ツリーを使用して、コードをデータとして解釈する動的なプログラムを作成し、そのコードに基づいて新しい機能を構築する方法についてまとめます。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 8088ce0c138cdb05a6e4a4fb6467e43efd252ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees-summary"></a>式ツリーのまとめ

[前へ -- 式の変換](expression-trees-translating.md)

このシリーズでは、*式ツリー*を使用して、コードをデータとして解釈する動的なプログラムを作成し、そのコードに基づいて新しい機能を構築する方法について説明してきました。

式ツリーを調べれば、アルゴリズムの目的を理解することができます。 そのコードを調べるだけではなく、 元のコードの変更バージョンを表す新しい式ツリーを構築することができます。

また式ツリーは、アルゴリズムを参照して、そのアルゴリズムを別の言語や環境に変換するためにも使用できます。 

## <a name="limitations"></a>制限事項

C# の新しい言語要素の中には、式ツリーに正しく変換できないものもあります。 式ツリーに `await` 式や `async` ラムダ式を含めることはできません。 C# 6 リリースで追加された機能の多くは、式ツリーで記述されたとおりには表示されません。 新しい機能は、等価の形式 (以前の構文) で式ツリーに公開されます。 このことは、それほど大きな制約にはならない場合もあります。 実際、式ツリーを解釈するコードは多くの場合、新しい言語機能が導入されても、以前と同様に動作します。

これらの制限事項があっても、式ツリーでは、データ構造として表されたコードの解釈や変更に依存する動的アルゴリズムを作成することが可能です。 式ツリーは強力なツールであり、Entity Framework などのリッチなライブラリで目的の機能を達成できる .NET エコシステムの 1 機能です。

