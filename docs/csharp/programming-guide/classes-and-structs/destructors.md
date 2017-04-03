---
title: "デストラクター (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ~ [C#], in destructors
- C# language, destructors
- destructors [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6940be34b6cc15f006901e6d14d2a38ebb5d012a
ms.lasthandoff: 03/13/2017

---
# <a name="destructors-c-programming-guide"></a>デストラクター (C# プログラミング ガイド)
デストラクターは、クラスのインスタンスを消滅させるために使用します。  
  
## <a name="remarks"></a>コメント  
  
-   デストラクターは、構造体には定義できません。 クラスでだけ使用します。  
  
-   クラスで使用できるデストラクターは 1 つだけです。  
  
-   デストラクターを継承またはオーバーロードすることはできません。  
  
-   デストラクターを呼び出すことはできません。 デストラクターは自動的に起動されます。  
  
-   デストラクターは修飾子を取らず、パラメーターはありません。  
  
 たとえば、次はクラス `Car` に対するデストラクターの宣言です。  
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  
  
 デストラクターは、オブジェクトの基底クラスで <xref:System.Object.Finalize%2A> を暗黙的に呼び出します。 したがって、前のデストラクターのコードは、暗黙的に次のコードに解釈されます。  
  
```  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 つまり、派生が最も多いクラスから派生が最も少ないクラスまで、継承チェーンのすべてのインスタンスに対して、`Finalize` メソッドが再帰的に呼び出されます。  
  
> [!NOTE]
>  空のデストラクターは使用しないでください。 デストラクターがクラスに存在するときは、エントリが `Finalize` キューで作成されます。 デストラクターを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。 デストラクターが空の場合、パフォーマンスを不必要に低下させるだけです。  
  
 デストラクターがいつ呼び出されるかはガベージ コレクターによって決定されるため、プログラマは制御できません。 ガベージ コレクターは、アプリケーションが使用していないオブジェクトをチェックします。 消滅できるオブジェクトと考えられる場合、デストラクター (存在する場合) を呼び出し、オブジェクトの格納に使用されているメモリを解放します。 デストラクターは、プログラムの終了時にも呼び出されます。  
  
 <xref:System.GC.Collect%2A> を呼び出すことによって、ガベージ コレクションを強制的に行うことができます。ただし、パフォーマンスに問題が発生する可能性があるため、通常はこの処理を避けます。  
  
## <a name="using-destructors-to-release-resources"></a>デストラクターを使ったリソースの解放  
 一般に C# では、ガベージ コレクションでランタイムにターゲットを設定しない言語で開発する場合ほど、メモリ管理を必要としません。 .NET Framework のガベージ コレクターが、オブジェクトに対するメモリの割り当てと解放を暗黙的に管理するからです。 ただし、ウィンドウ、ファイル、ネットワーク接続などのアンマネージ リソースをアプリケーションでカプセル化するとき、デストラクターを使ってこれらのリソースを解放する必要があります。 オブジェクトを消滅させることができるとき、ガベージ コレクターはそのオブジェクトの `Finalize` メソッドを実行します。  
  
## <a name="explicit-release-of-resources"></a>リソースの明示的な解放  
 アプリケーションで高額な外部リソースを使用している場合、ガベージ コレクターがオブジェクトを解放する前にリソースを明示的に解放する手段を用意することが推奨されます。 この処理を行うには、オブジェクトに対して必要なクリーンアップを実行する `Dispose` メソッドを <xref:System.IDisposable> インターフェイスから実装します。 これによって、アプリケーションのパフォーマンスを大幅に向上させることができます。 このようにリソースを明示的に制御する場合でも、デストラクターは、`Dispose` メソッドの呼び出しが失敗したときにリソースをクリーンアップするための安全装置になります。  
  
 リソースのクリーンアップの詳細については、次のトピックを参照してください。  
  
-   [アンマネージ リソースのクリーンアップ](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213)  
  
-   [Dispose メソッドの実装](http://msdn.microsoft.com/library/eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9)  
  
-   [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>例  
 次の例では、継承チェーンを形成する 3 つのクラスを作成します。 `First` が基底クラスであり、`Second` は `First` から派生し、`Third` は `Second` から派生します。 3 つのクラスのいずれにもデストラクターがあります。 `Main()` では、派生が最も多いクラスのインスタンスが作成されます。 プログラムを実行すると、3 つのクラスのデストラクターが派生が最も多いクラスから派生が最も少ないクラスの順に自動的に呼び出されます。  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IDisposable>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [ガベージ コレクション](../../../standard/garbagecollection/index.md)
