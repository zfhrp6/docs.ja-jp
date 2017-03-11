---
title: "Using Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.using"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "resource disposal"
  - "Try...Catch...Finally statements, equivalent to Using statement"
  - "resources [Visual Basic], disposing"
  - "Using statement"
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 36
---
# Using Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Using` ブロックの開始を宣言し、オプションでこのブロックが制御するシステム リソースを取得します。  
  
## 構文  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`resourcelist`|`resourceexpression` を指定しない場合は必ず指定します。  コンマで区切られた一つ以上のシステム リソースのリスト `Using` のこのブロックが制御する。|  
|`resourceexpression`|`resourcelist` を指定しない場合は必ず指定します。  この `Using` ブロックによって制御されるシステム リソースを参照する参照変数または式です。|  
|`statements`|省略可能。  `Using` ブロックが実行するステートメントのブロックです。|  
|`End Using`|必須。  `Using` ブロックの定義を終了し、制御しているすべてのリソースを破棄します。|  
  
 `resourcelist` 部分のリソースは、次の構文と指定項目で指定します。  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 または  
  
 `resourcename As resourcetype = resourceexpression`  
  
## resourcelist の指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`resourcename`|必須。  `Using` ブロックが制御するシステム リソースを参照する参照変数です。|  
|`New`|`Using` ステートメントがリソースを取得する場合は、必ず指定します。  リソースを既に取得している場合は、2 つ目の構文を使用してください。|  
|`resourcetype`|必須。  リソースのクラス。  このクラスは、<xref:System.IDisposable> インターフェイスを実装する必要があります。|  
|`arglist`|省略可能。  `resourcetype` のインスタンスを作成するために、コンストラクターに渡す引数のリストです。  「[Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|  
|`resourceexpression`|必須。  `resourcetype` の要件を満たすシステム リソースを参照する変数または式です。  2 番目の構文を使用する場合は、制御を `Using` ステートメントに渡す前にリソースを取得する必要があります。|  
  
## 解説  
 ファイル ハンドル、COM ラッパー、SQL 接続などのアンマネージ リソースを取得するコードを作成する場合があります。  そのようなコードに `Using` ブロックを使用すると、リソースを使い終わったとき、その 1 つ以上のリソースを確実に破棄できます。  これにより、他のコードからそれらのリソースを使うことが可能になります。  
  
 マネージ リソースであれば、何もコードを追加しなくても、.NET Framework のガベージ コレクター \(GC\) が破棄してくれます。  マネージ リソースに `Using` ブロックは必要ありません。  ただし、`Using` ブロックを使用して、ガベージ コレクターを待たずに、マネージ リソースの破棄を強制することはできます。  
  
 `Using` ブロックは、取得、使用、破棄という 3 つの部分で構成されます。  
  
-   *取得*システム リソースを参照するための変数を作成、および初期化します。  `Using` ステートメントでは 1 つ以上のリソースを取得することも、ブロックに入る前にリソースを 1 つ取得して、それを `Using` ステートメントに指定することもできます。  `resourceexpression` を指定する場合は、制御を `Using` ステートメントに渡す前にリソースを取得する必要があります。  
  
-   *使用*リソースにアクセスし、それを使って処理を実行します。  リソースを使用するステートメントは、`Using` と `End Using` の間に記述します。  
  
-   *破棄* `resourcename` に指定されたオブジェクトから <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。  これによって、オブジェクトはリソースを適切に終了させることができます。  `End Using` ステートメントはリソースを `Using` ブロックの制御に基づいて破棄します。  
  
## \[動作\]  
 `Using` ブロックは `Try`...`Finally` 構造 \(`Try` でリソースを使用し、`Finally` ブロックでリソースを破棄する\) と同様に動作します。  このため、`Using` ブロックを使えば、ブロックがどのように終了した場合でも、リソースは必ず破棄されます。  これは、<xref:System.StackOverflowException> を除く未処理の例外の場合にも該当します。  
  
 `Using` ステートメントによって取得されるリソース変数のスコープは、必ず `Using` ブロックに制限されます。  
  
 `Using` ステートメントで 1 つ以上のシステム リソースを指定すると、`Using` ブロックを入れ子にするのと同じ意味になります。  
  
 `resourcename` が `Nothing`場合、<xref:System.IDisposable.Dispose%2A> の呼び出しは行われず、例外はスローされません。  
  
## Using ブロック内の構造化例外処理  
 `Using` ブロック内で起きる可能性のある例外を処理することが必要な場合は、ブロック内に `Try`...`Finally` 構造全体を追加してください。  `Using` ステートメントがリソースの取得に失敗するケースに対応する必要がある場合は、`resourcename` が `Nothing` であるかどうかをテストします。  
  
## Using ブロック以外での構造化例外処理  
 リソースの取得を細かく制御する必要がある場合、または `Finally` ブロックにコードを追加する必要がある場合は、`Using` ブロックを `Try`...`Finally` 構造に書き換えてください。  次に示すスケルトンは、どちらも `resource` の取得と破棄の処理を実行する `Try` 構造と `Using` 構造の例です。  
  
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
>  `Using` ブロック内のコードで、`resourcename` に含まれるオブジェクトを別の変数に割り当てることはできません。  `Using` ブロックの終了時にリソースが破棄され、他の変数は自分がポイントしているリソースにアクセスできなくなります。  
  
## 使用例  
 次の例は、log.txtという作成して2行のテキストをファイルに書き込みます。  この例では、と同じファイルを読み取り、行のテキストが表示されます。  
  
 <xref:System.IO.TextWriter> と <xref:System.IO.TextReader> のクラスが <xref:System.IDisposable> のインターフェイスを実装するため、コードは、ファイルが読み取りおよび書き込み操作の後で正しく閉じるように `Using` のステートメントを使用できます。  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/using-statement_1.vb)]  
  
## 参照  
 <xref:System.IDisposable>   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [How to: Dispose of a System Resource](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)