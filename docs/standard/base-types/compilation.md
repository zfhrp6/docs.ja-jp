---
title: "正規表現におけるコンパイルと再利用"
description: "正規表現におけるコンパイルと再利用"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3adea434-e2ed-4023-b4f5-b0608b4cf53f
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 1832403174276e48dc1857be8ff11fba2b9a250c

---

# <a name="compilation-and-reuse-in-regular-expressions"></a>正規表現におけるコンパイルと再利用

正規表現エンジンが式をどのようにコンパイルするか、および正規表現がどのようにキャッシュされるかを理解することで、正規表現を幅広く使用するアプリケーションのパフォーマンスを最適化できます。 このトピックでは、コンパイルとキャッシュの両方について説明します。

## <a name="compiled-regular-expressions"></a>コンパイルされた正規表現

既定では、正規表現エンジンは、内部命令のシーケンス (Microsoft 中間言語 (MSIL) とは異なる高度なコード) に正規表現をコンパイルします。 エンジンは、正規表現を実行するときに内部コードを解釈します。

[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを使用して [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトを構築した場合、このオブジェクトは、高度な正規表現の内部命令ではなく明示的な MSIL コードに正規表現をコンパイルします。 これにより、.NET の Just-In-Time (JIT) コンパイラは、式をネイティブのマシン コードに変換してパフォーマンスを高めることができます。

ただし、生成された MSIL をアンロードすることはできません。 コードをアンロードする唯一の方法は、アプリケーション ドメイン全体をアンロードする (つまり、アプリケーションのすべてのコードをアンロードする) ことです。 実際には、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを使用して正規表現をコンパイルすると、[Regex](xref:System.Text.RegularExpressions.Regex) オブジェクト (それ自体がガベージ コレクションに解放される) によって正規表現が作成された場合でも、.NET は、コンパイルされた式で使用されるリソースを解放することはありません。

リソースを過剰に消費することがないよう、[RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) オプションを使用してコンパイルするさまざまな正規表現の数を慎重に制限する必要があります。 アプリケーションで多数または無制限の数の正規表現を使用しなければならない場合は、各式をコンパイルするのではなく、解釈する必要があります。 ただし、少数の正規表現が繰り返し使用される場合は、パフォーマンスを高めるために [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) を使用してコンパイルする必要があります。 

## <a name="the-regular-expressions-cache"></a>正規表現のキャッシュ

パフォーマンスを高めるために、正規表現エンジンは、コンパイルされた正規表現のアプリケーション全体のキャッシュを保持します。 キャッシュは、静的メソッド呼び出しでのみ使用される正規表現パターンを格納します (インスタンス メソッドに渡される正規表現パターンはキャッシュされません)。これにより、式を使用するたびに高度なバイト コードに再解析する必要がなくなります。

キャッシュされる正規表現の最大数は、`static` (Visual Basic では `Shared`) [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) プロパティの値によって決定されます。 既定では、正規表現エンジンは最大 15 個のコンパイルされた正規表現をキャッシュします。 コンパイルされた正規表現の数がキャッシュ サイズを超えた場合は、最近の使用頻度が最も低い正規表現が破棄され、新しい正規表現がキャッシュされます。 

アプリケーションでは、次の 2 つの方法のいずれかでプリコンパイル済みの正規表現を利用できます。

* [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトの静的メソッドを使用して、正規表現を定義する。 別の静的メソッド呼び出しで既に定義されている正規表現パターンを使用している場合、正規表現エンジンはこれをキャッシュから取得します。 そうでない場合、エンジンは正規表現をコンパイルしてキャッシュに追加します。

* 既存の [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトの正規表現パターンが必要な間、このオブジェクトを再利用する。


オブジェクトのインスタンス化および正規表現のコンパイルのオーバーヘッドが原因となり、さまざまな [Regex](xref:System.Text.RegularExpressions.Regex) オブジェクトを作成してすぐに破棄するプロセスは非常にコストがかかります。 多数の異なる正規表現を使用するアプリケーションの場合は、静的 [Regex](xref:System.Text.RegularExpressions.Regex) メソッドの呼び出しを使用することで、および場合によっては正規表現キャッシュのサイズを大きくすることで、パフォーマンスを最適化できます。

## <a name="see-also"></a>関連項目

[.NET 正規表現](regular-expressions.md)




<!--HONumber=Nov16_HO1-->


