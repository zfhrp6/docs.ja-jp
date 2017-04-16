---
title: "例外階層 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "例外の種類"
  - "ランタイム例外"
  - "基本例外"
  - "ApplicationException クラス"
  - "共通言語ランタイム例外"
  - "COM 相互運用, 例外"
  - "例外階層"
ms.assetid: f7d68675-be06-40fb-a555-05f0c5a6f66b
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# 例外階層
例外は、実行中のプログラムによって生成される例外と、共通言語ランタイムによって生成される例外の&2; 種類に分類されます。 さらに、アプリケーションまたはランタイムによってスロー可能な例外の階層もあります。  
  
 <xref:System.Exception?displayProperty=fullName>クラスは、例外の基底クラスです。 いくつかの例外クラスから直接継承<xref:System.Exception>も含め、 <xref:System.ApplicationException>と<xref:System.SystemException>します。 これらの&2; つのクラスがほぼすべてのランタイム例外の基礎を成しています。  
  
 ほとんどの例外から直接派生した<xref:System.Exception>ない機能、および新しいメンバーを追加します。 たとえば、 <xref:System.InvalidCastException>クラスの階層構造を次に示します。  
  
 <xref:System.Object><xref:System.Exception> <xref:System.SystemException> <xref:System.InvalidCastException>  
  
 ランタイムの適切な派生クラスをスローする<xref:System.SystemException>エラーが発生したとき。 このようなエラーは、実行時チェックのエラー (配列範囲外エラーなど) が原因で発生します。また、任意のメソッドの実行中に発生することがあります。 新しい例外を作成するアプリケーションをデザインする場合からそれらの例外を派生する必要があります、<xref:System.Exception>クラスです。 キャッチすることはお勧めできません、 <xref:System.SystemException>でもなく、プログラミングをスローすることをお勧め、 <xref:System.SystemException>アプリケーションにします。  
  
 最も重大な例外、または回復不可能な状態で、ランタイムによってスローされた — を含める<xref:System.ExecutionEngineException>、 <xref:System.StackOverflowException>と<xref:System.OutOfMemoryException>します。  
  
 相互運用の例外の派生元<xref:System.SystemException>によってさらに拡張および<xref:System.Runtime.InteropServices.ExternalException>します。 たとえば、 <xref:System.Runtime.InteropServices.COMException> COM 相互運用機能の操作中にスローされる例外は、その派生元で<xref:System.Runtime.InteropServices.ExternalException>します。 <xref:System.ComponentModel.Win32Exception>と<xref:System.Runtime.InteropServices.SEHException>からも派生<xref:System.Runtime.InteropServices.ExternalException>します。  
  
## <a name="hierarchy-of-runtime-exceptions"></a>ランタイム例外の階層  
 ランタイムに起因する例外の基本セット<xref:System.SystemException>個々 の命令を実行するときにそれをスローします。 次の表に、ランタイムから提供される標準例外と、派生クラスを作成する場合の条件を階層の順番に示します。  
  
|例外の種類|基本型|説明|例|  
|--------------------|---------------|-----------------|-------------|  
|[例外](../../../docs/standard/exceptions/exception-class-and-properties.md)|<xref:System.Object>|すべての例外の基底クラスです。|なし (この例外の派生クラスを使用)。|  
|<xref:System.SystemException>|<xref:System.Exception>|ランタイムで生成されるすべてのエラーの基底クラスです。|なし (この例外の派生クラスを使用)。|  
|<xref:System.IndexOutOfRangeException>|<xref:System.SystemException>|配列のインデックスが誤っている場合にのみ、ランタイムによってスローされます。|次のように、配列に対して配列の有効範囲外のインデックスを付けた場合。<br /><br /> `var i = arr[arr.Length + 1];`<br /><br /> `Dim i = arr(arr.Length + 1)`|  
|<xref:System.NullReferenceException>|<xref:System.SystemException>|null オブジェクトが参照された場合にのみ、ランタイムによってスローされます。|`object o = null; string s = o.ToString();`<br /><br /> `Dim o As Object = Nothing Dim s As String = o.ToString()`|  
|<xref:System.AccessViolationException>|<xref:System.SystemException>|無効なメモリがアクセスされた場合にのみ、ランタイムによってスローされます。|アンマネージ コードまたは安全でないマネージ コードと相互運用されていて、無効なポインターが使用された場合に発生します。|  
|<xref:System.InvalidOperationException>|<xref:System.SystemException>|無効な状態の場合にメソッドによってスローされます。|列挙子の呼び出し`GetNext`基になるコレクションから項目を削除した後のメソッドです。|  
|<xref:System.ArgumentException>|<xref:System.SystemException>|すべての引数の例外の基底クラスです。|なし (この例外の派生クラスを使用)。|  
|<xref:System.ArgumentNullException>|<xref:System.ArgumentException>|null の引数を許可しないメソッドによってスローされます。|`String s = null; int i = "Calculate".IndexOf(s);`<br /><br /> `Dim s As String = Nothing Dim i As Integer = "Calculate".IndexOf(s)`|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.ArgumentException>|引数が特定の範囲内にあることを検査するメソッドによってスローされます。|`String s = "string"; s = s.Substring(s.Length + 1);`<br /><br /> `Dim s As String = "string" s = s.Substring(s.Length + 1)`|  
|<xref:System.Runtime.InteropServices.ExternalException>|<xref:System.SystemException>|ランタイム外部の環境で発生した例外、およびランタイム外部の環境で対象とされる例外の基底クラスです。|なし (この例外の派生クラスを使用)。|  
|<xref:System.Runtime.InteropServices.COMException>|<xref:System.Runtime.InteropServices.ExternalException>|COM HRESULT 情報をカプセル化する例外です。|COM 相互運用機能で使用されます。|  
|<xref:System.Runtime.InteropServices.SEHException>|<xref:System.Runtime.InteropServices.ExternalException>|Win32 構造化例外処理情報をカプセル化する例外です。|アンマネージ コード相互運用機能で使用されます。|  
  
## <a name="see-also"></a>関連項目  
 [Exception クラスとプロパティ](../../../docs/standard/exceptions/exception-class-and-properties.md)   
 [例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [例外の推奨事項](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [例外](../../../docs/standard/exceptions/index.md)