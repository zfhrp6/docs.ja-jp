---
title: "方法: 式ツリーを使用して動的クエリ (Visual Basic) を作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>方法: 式ツリーを使用して動的クエリ (Visual Basic) を作成するには
LINQ では、式ツリーを使用して、そのターゲット データ ソースの<xref:System.Linq.IQueryable%601>。</xref:System.Linq.IQueryable%601>を実装する構造化されたクエリを表す たとえば、LINQ プロバイダーを実装する、<xref:System.Linq.IQueryable%601>リレーショナル データ ストアを照会するためのインターフェイス</xref:System.Linq.IQueryable%601>。 Visual Basic コンパイラでは、実行時の式ツリーをビルドするコードにこのようなデータ ソースをターゲットとするクエリをコンパイルします。 クエリ プロバイダーは、式ツリー データ構造をスキャンし、それをデータ ソースの適切なクエリ言語に変換します。  
  
 式ツリーが LINQ で<xref:System.Linq.Expressions.Expression%601>。</xref:System.Linq.Expressions.Expression%601>型の変数に割り当てられているラムダ式を表すも使用します。  
  
 このトピックでは、式ツリーを使用して、動的な LINQ クエリを作成する方法について説明します。 動的クエリは、クエリの詳細については、コンパイル時に不明な場合に便利です。 たとえば、アプリケーションは、エンド ユーザー データをフィルター処理する&1; つまたは複数の述語を指定することができるユーザー インターフェイスを提供する可能性があります。 クエリに LINQ を使用するためにこのようなアプリケーションは、実行時に、LINQ クエリを作成するのに式ツリーを使用する必要があります。  
  
## <a name="example"></a>例  
 次の例は、式ツリーを使用してに対するクエリを作成する方法を表示、`IQueryable`データ ソースおよびそれを実行します。 コードでは、次のクエリを表す式ツリーを作成します。  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 工場出荷時のメソッド、<xref:System.Linq.Expressions>名前空間は、クエリ全体を構成する式を表す式ツリーの作成に使用されます</xref:System.Linq.Expressions>。 標準クエリ演算子メソッドの呼び出しを表す式を参照してください、<xref:System.Linq.Queryable>これらのメソッドの実装</xref:System.Linq.Queryable>。 最後の式ツリーが渡される、<xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>のプロバイダーの実装、`IQueryable`型の実行可能ファイルのクエリを作成するデータ ソース`IQueryable`</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>。 結果を取得するには、そのクエリ変数を列挙します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 このコードに渡される述語の式の数を使用して、`Queryable.Where`メソッドです。 ただし、ユーザー入力に依存する可変個の述語式を結合するアプリケーションを記述することができます。 ユーザーからの入力に応じて、クエリで呼び出される標準クエリ演算子を変更することもできます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   新しい**コンソール アプリケーション**プロジェクトです。  
  
-   参照されていない場合は、System.Core.dll への参照を追加します。  
  
-   System.Linq.Expressions 名前空間が含まれます。  
  
-   例のコードをコピーして貼り付けます、 `Main` `Sub`プロシージャです。  
  
## <a name="see-also"></a>関連項目  
 [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [方法: 式ツリー (Visual Basic) を実行](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
