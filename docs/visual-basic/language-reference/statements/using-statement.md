---
title: Using ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 725eeb42dc5462022ac1a021c537d701929398ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604966"
---
# <a name="using-statement-visual-basic"></a>Using ステートメント (Visual Basic)
始まりを宣言、`Using`をブロックし、必要に応じてブロックを制御するシステム リソースを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`resourcelist`|指定しないかどうかに必要な`resourceexpression`します。 この 1 つまたは複数のシステム リソースの一覧表示`Using`コントロール、コンマで区切ってをブロックします。|  
|`resourceexpression`|指定しないかどうかに必要な`resourcelist`します。 参照変数またはこので制御するシステム リソースを参照する式`Using`ブロックします。|  
|`statements`|任意。 ステートメントのブロックを`Using`ブロックが実行されます。|  
|`End Using`|必須。 定義を終了、`Using`ブロックおよびそれによって制御されるすべてのリソースを破棄します。|  
  
 内の各リソース、`resourcelist`部分は、次の構文とパーツ。  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 - または -  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a>resourcelist 部分  
  
|用語|定義|  
|---|---|  
|`resourcename`|必須。 システム リソースを参照する参照変数を`Using`コントロールをブロックします。|  
|`New`|必要な場合、`Using`ステートメントがリソースを取得します。 リソースを既に取得した場合は、2 番目の構文を使用します。|  
|`resourcetype`|必須。 リソースのクラスです。 このクラスを実装する必要があります、<xref:System.IDisposable>インターフェイスです。|  
|`arglist`|任意。 インスタンスを作成するコンス トラクターに渡す引数のリスト`resourcetype`です。 参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。|  
|`resourceexpression`|必須。 変数または式の要件を満たすシステム リソースを参照する`resourcetype`です。 2 番目の構文を使用する場合は、制御を渡す前に、リソースを取得する必要があります、`Using`ステートメントです。|  
  
## <a name="remarks"></a>コメント  
 場合によって、コードでは、ファイル ハンドル、COM ラッパーの場合は、SQL 接続など、アンマネージ リソースが必要です。 A`Using`ブロックがそれらにコードが完了すると、そのような 1 つまたは複数のリソースの破棄を保証します。 これによりを使用するには、他のコードで使用可能です。  
  
 マネージ リソースが破棄、.NET Framework ガベージ コレクター (GC) によって、手動で追加のコーディングなし。 必要としない、`Using`マネージ リソースをブロックします。 ただし、引き続き使用できます、`Using`強制的にガベージ コレクターを待つ代わりにマネージ リソースの破棄をブロックします。  
  
 A`Using`ブロックには 3 つの部分。 取得、使用状況、および破棄します。  
  
-   *買収*変数の作成と初期化、システムのリソースを参照することを意味します。 `Using`ステートメントが 1 つまたは複数のリソースを取得するか、ブロックに入る前にリソースを 1 つを取得してそれを指定する、`Using`ステートメントです。 指定した場合`resourceexpression`に制御を渡す前に、リソースを取得する必要があります、`Using`ステートメントです。  
  
-   *使用状況*リソースにアクセスし、それを使ってアクションを実行することを意味します。 間にあるステートメント`Using`と`End Using`リソースの使用量を表します。  
  
-   *廃棄*を呼び出す方法、<xref:System.IDisposable.Dispose%2A>メソッド内のオブジェクトを`resourcename`です。 これにより、そのリソースを正常に終了するオブジェクト。 `End Using`下にあるリソースを破棄するステートメント、`Using`ブロックのコントロールです。  
  
## <a name="behavior"></a>動作  
 A`Using`ブロックの動作と同様に、`Try`しています.`Finally`を構築、`Try`ブロックは、リソースを使用して、`Finally`それらのブロックを破棄します。 このため、`Using`ブロック、ブロックを終了する方法に関係なく、リソースの破棄を保証します。 これは、未処理の例外を場合でも当てはまりますを除き、<xref:System.StackOverflowException>です。  
  
 によって取得されたすべてのリソース変数のスコープ、`Using`ステートメントに制限されます、`Using`ブロックします。  
  
 1 つ以上のシステム リソースを指定する場合、`Using`を入れ子にする場合と同じステートメントでは、影響は`Using`互いをブロックします。  
  
 場合`resourcename`は`Nothing`、呼び出しがありません<xref:System.IDisposable.Dispose%2A>が行われると、例外はスローされません。  
  
## <a name="structured-exception-handling-within-a-using-block"></a>構造化例外処理を使用してブロック内  
 内で発生する可能性がある例外を処理する必要があるかどうか、`Using`ブロック、完全なを追加することができます`Try`しています.`Finally`を構築します。 ケースを処理する必要がある場合で、`Using`ステートメントが、リソースの取得中に失敗した、かどうかをテストできます`resourcename`は`Nothing`します。  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a>構造化例外処理を使用してブロックではなく  
 場合は、リソースの取得をより細かく制御する必要がありますまたはでコードを追加する必要があります、`Finally`ブロックを書き直すことができます、`Using`としてブロック、`Try`しています.`Finally`構築します。 次の例では、スケルトン`Try`と`Using`買収や破棄が同じ構造`resource`です。  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  内のコード、`Using`ブロック内のオブジェクトを割り当てないでください`resourcename`を別の変数です。 終了すると、`Using`ブロック、リソースが破棄され、他の変数が指すリソースにアクセスできません。  
  
## <a name="example"></a>例  
 次の例では、log.txt は、ファイルに次の 2 つの行のテキストを書き込むファイルを作成します。 例もその同じファイルをテキストの行が表示されます。  
  
 <xref:System.IO.TextWriter>と<xref:System.IO.TextReader>クラスで実装、<xref:System.IDisposable>コードで使用できるインターフェイス、`Using`ステートメント ファイルの書き込みの後に閉じられたし、読み取り操作は正しくことを確認します。  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IDisposable>  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [方法 : システム リソースを破棄する](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
