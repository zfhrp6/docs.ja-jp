---
title: "リフレクション (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ae042933575849e105d7b681634a61319c1d6ee
ms.lasthandoff: 03/13/2017

---
# <a name="reflection-visual-basic"></a>リフレクション (Visual Basic)
リフレクション オブジェクトの提供 (型の<xref:System.Type>) アセンブリ、モジュールや型を記述する</xref:System.Type>。 リフレクションを使用して、動的に型のインスタンスを作成、既存のオブジェクトにバインドまたは既存のオブジェクトから型を取得し、メソッドの呼び出しまたは、フィールドやプロパティにアクセスすることができます。 コード内の属性を使用している場合は、リフレクションを使用してアクセスします。 詳細については、次を参照してください。[属性](https://msdn.microsoft.com/library/5x6cd29c)します。  
  
 静的メソッドを使用してリフレクションの単純な例を次に示します`GetType`- からすべての型によって継承された、`Object`基本クラスの変数の型を取得します。  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 出力です。  
  
 `System.Int32`  
  
 次の例では、リフレクションを使用して、読み込まれたアセンブリの完全名を取得します。  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 出力です。  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>リフレクションの概要  
 リフレクションは、次のような場合に便利です。  
  
-   プログラムのメタデータ内の属性にアクセスする必要がある場合。 詳細については、次を参照してください。[を取得する情報を属性に格納](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)します。  
  
-   調べることと、アセンブリ内の型をインスタンス化します。  
  
-   実行時に新しい型を構築します。 <xref:System.Reflection.Emit>。</xref:System.Reflection.Emit>クラスを使用します。  
  
-   実行時に作成された型のメソッドへのアクセスの遅延バインディングを実行します。 トピックを参照して[動的な読み込みおよび使用して型](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc)します。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [リフレクション](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [型情報の表示](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [リフレクションとジェネリック型](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <xref:System.Reflection.Emit></xref:System.Reflection.Emit>  
  
-   [属性に格納されている情報を取得します。](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md)   
 [共通言語ランタイムのアセンブリ](https://msdn.microsoft.com/library/k3677y81)
