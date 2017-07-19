---
title: "Assert メソッドの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Assert メソッド"
  - "アサートされたアクセス許可"
  - "呼び出し元のセキュリティ チェック"
  - "コード アクセス セキュリティ, オーバーライド (セキュリティ チェックの)"
  - "付与 (アクセス許可の), オーバーライド (セキュリティ チェックの)"
  - "オーバーライド (セキュリティ チェックの)"
  - "アクセス許可 [.NET Framework], アサーション"
  - "アクセス許可 [.NET Framework], オーバーライド (セキュリティ チェックの)"
  - "セキュリティ [.NET Framework], アサーション"
  - "セキュリティ [.NET Framework], オーバーライド (セキュリティ チェックの)"
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
caps.latest.revision: 20
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 18
---
# Assert メソッドの使用
<xref:System.Security.CodeAccessPermission.Assert%2A> は、コードのアクセス許可のクラスおよび <xref:System.Security.PermissionSet>クラスで呼び出すことができるメソッドです。  **Assert** を使用すると、コード \(および下流の呼び出し元\) が、コードには実行のアクセス許可があるものの、その呼び出し元には実行のアクセス許可がない可能性がある操作を実行できるようになります。  セキュリティ アサーションは、セキュリティ チェック時にランタイムが実行する正常なプロセスを変更します。  アクセス許可をアサートすると、アサートされたアクセス許可のためにコードの呼び出し元をチェックしないようセキュリティ システムに指示します。  
  
> [!CAUTION]
>  アサーションはセキュリティ ホールを開き、セキュリティの制限事項を適用するランタイムのメカニズムを弱体化させる可能性があるため、慎重に使用してください。  
  
 アサーションは、ライブラリがアンマネージ コードを呼び出す状況、またはライブラリの使用目的と明らかに関係のないアクセス許可を必要とする呼び出しを行う状況に役立ちます。  たとえば、アンマネージ コードを呼び出すすべてのマネージ コードには、**UnmanagedCode** フラグが指定された **SecurityPermission** が含まれている必要があります。  ローカルのイントラネットからダウンロードするコードなど、ローカル コンピューターから発生していないコードには、既定でこのアクセス許可は付与されません。  そのため、ローカルのイントラネットからダウンロードするコードがアンマネージ コードを使用するライブラリを呼び出せるようにするには、ライブラリによってアサートされたアクセス許可がコードに指定されている必要があります。  さらに、ライブラリによっては呼び出し元からは見えない呼び出し、および特別なアクセス許可を必要とする呼び出しを行う場合があります。  
  
 また、コードが呼び出し元から完全に非表示にされる方法でリソースにアクセスする状況において、アサーションを使用することもできます。  たとえば、ライブラリがデータベースから情報を取得しますが、プロセス内でコンピューターのレジストリからも情報を読み取ると仮定してください。  ライブラリを使用する開発者は、ソースにアクセスできないため、開発者のコードがユーザーのコードを使用するために **RegistryPermission** を必要としていることを知る方法がありません。  この場合、コードの呼び出し元がレジストリへのアクセス許可を持つことを求めるのは妥当でないか不必要と判断した場合は、レジストリを読み取るアクセス許可をアサートすることができます。  この状況では、**RegistryPermission** がない呼び出し元がライブラリを使用できるように、ライブラリがアクセス許可をアサートすることが適切です。  
  
 アサーションがスタック ウォークに影響を与えるのは、アサートされたアクセス許可および下流の呼び出し元によって要求されるアクセス許可が同じ型である場合、かつ要求されたアクセス許可がアサートされているアクセス許可のサブセットである場合のみです。  たとえば、**FileIOPermission** を C ドライブのすべてのファイルを読み取るようにアサートする場合、かつ **FileIOPermission** に対して C:\\Temp 内のファイルを読み取る下流からの要求が行われた場合、アサーションはスタック ウォークに影響を与える可能性があります。 ただし、要求が **FileIOPermission** に対して C ドライブに書き込む要求であった場合、アサーションの影響はありません。  
  
 アサーションを実行する場合、コードにアサートしているアクセス許可と、アサーションを実行する権利を表す <xref:System.Security.Permissions.SecurityPermission> の両方が付与されている必要があります。  コードに付与されていないアクセス許可をアサートすることができますが、アサーションがセキュリティ チェックを成功させようとする前にセキュリティ チェックが失敗するため、アサーションが無意味になってしまいます。  
  
 次の図は、**Assert** を使用する際に発生することを示しています。  次のステートメントについて、アセンブリ A、B、C、E、および F が true であり、P1 と P1A という 2 つのアクセス許可があると仮定してください。  
  
-   P1A は C ドライブ上の .txt ファイルを読み取る権限を表します。  
  
-   P1 は C ドライブ上のすべてのファイルを読み取る権限を表します。  
  
-   P1A と P1 はいずれも**FileIOPermission** 型で、P1A は P1 のサブセットです。  
  
-   アセンブリ E と F には P1A のアクセス許可が付与されています。  
  
-   アセンブリ C には P1 のアクセス許可が付与されています。  
  
-   アセンブリ A と B には P1 と P1A のアクセス許可のいずれも付与されていません。  
  
-   メソッド A はアセンブリ A 内にあり、メソッド B はアセンブリ B 内にあり、以下同様です。  
  
 ![](../../../docs/framework/misc/media/assert.gif "assert")  
Assert の使用  
  
 このシナリオでは、メソッド A が B を呼び出し、B が C、C が E、E が F をそれぞれ呼び出します。  メソッド C は C ドライブ上のファイルを読み取るアクセス許可 \(P1 のアクセス許可\) をアサートします。メソッド E は C ドライブ上の .txt ファイルを読み取るアクセス許可 \(P1A のアクセス許可\) を要求します。  実行時に F で要求が発生した場合、E から開始して F の全呼び出し元のアクセス許可をチェックするスタック ウォークが実行されます。  E には P1A のアクセス許可が付与されているため、スタック ウォークは、C のアサーションが発見された C のアクセス許可を調べるために続行します。  要求されたアクセス許可 \(P1A\) は、アサートされたアクセス許可 \(P1\) のサブセットであるため、スタック ウォークが停止し、セキュリティ チェックは自動的に成功します。  アセンブリ A と B に P1A のアクセス許可が付与されていないことは関係ありません。  P1 をアサートすることで、メソッド C は、呼び出し元がそのリソースへのアクセス許可を付与されていない場合でも呼び出し元が、P1 で保護されているリソースにアクセスできることを保証します。  
  
 クラス ライブラリをデザインし、クラスが保護されたリソースにアクセスする場合は、ほとんどの場合、呼び出し元のクラスが適切なアクセス許可を持つことを求めるセキュリティの要求を行う必要があります。  ほとんどの呼び出し元がアクセス許可を持たないことが分かっている操作をクラスが実行する場合、かつこれらの呼び出し元が自分のコードを呼び出すことへの責任を進んで負う場合は、コードが実行している操作を表すアクセス許可のオブジェクトにある **Assert** メソッドを呼び出してアクセス許可をアサートすることができます。  このように **Assert** を使用すると、通常はそのようにできなかった呼び出し元がコードを呼び出すことができます。  そのため、アクセス許可をアサートする場合、自分のコンポーネントが誤使用されるのを防ぐために、必ず事前に適切なセキュリティ チェックを実行する必要があります。  
  
 たとえば、信頼性の高いライブラリのクラスにファイルを削除するメソッドがあると仮定します。  メソッドは、アンマネージ Win32 関数を呼び出してファイルにアクセスします。  呼び出し元は、コードの **Delete** メソッドを呼び出して、削除するファイルの名前 C:\\Test.txt を渡します。  **Delete** メソッド内で、コードは C:\\Test.txt への書き込みのアクセス権を表す <xref:System.Security.Permissions.FileIOPermission> オブジェクトを作成します。  \(ファイルを削除するには書き込みのアクセス権が必要です。\) コードは、**FileIOPermission** オブジェクトの **Demand** メソッドを呼び出して強制セキュリティ チェックを呼び出します。  コール スタックのいずれかの呼び出し元にこのアクセス許可がない場合は、<xref:System.Security.SecurityException> がスローされます。  例外がスローされない場合、すべての呼び出し元に C:\\Test.txt へのアクセス権があることがわかります。  ほとんどの呼び出し元はアンマネージ コードへのアクセス許可が得られないと考えられるため、コードはアンマネージ コードを呼び出す権限を表す <xref:System.Security.Permissions.SecurityPermission> オブジェクトを作成し、オブジェクトの **Assert** メソッドを呼び出します。  最後に、コードは C:\\Text.txt を削除するアンマネージ Win32 関数を呼び出し、呼び出し元にコントロールを返します。  
  
> [!CAUTION]
>  そこで、アサートするためのアクセス許可によって保護されているリソースにアクセスするために自分のコードが他のコードによって使用される状況では、自分のコードでアサーションが使用されていないことを確認する必要があります。  たとえば、あるファイルに書き込むコードにおいて、そのファイル名が呼び出し元によってパラメーターとして指定されている場合は、ファイルに書き込むために **FileIOPermission** をアサートしないでください。コードが第三者によって開かれ、悪用される可能性があるためです。  
  
 強制セキュリティ構文を使用する場合、同じメソッドで複数のアクセス許可の下で **Assert** メソッドを呼び出すと、セキュリティ例外がスローされます。  代わりに、**PermissionSet** オブジェクトを作成し、これに呼び出す個別のアクセス許可を渡してから、**PermissionSet** オブジェクトの **Assert** メソッドを呼び出します。  宣言型のセキュリティ構文を使用する場合は、**Assert** メソッドを複数回呼び出すことができます。  
  
 次の例は、**Assert** メソッドを使用したセキュリティ チェックをオーバーライドする宣言型の構文を示しています。  **FileIOPermissionAttribute** 構文では 2 つの値 \(<xref:System.Security.Permissions.SecurityAction> 列挙体、およびアクセス許可が付与されるファイルまたはディレクトリの場所\) を指定することに注意してください。  呼び出し元がファイルへのアクセス許可のチェックを受けていない場合でも、**Assert** への呼び出しにより、`C:\Log.txt` へのアクセスの要求は成功します。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 次のコード フラグメントは、**Assert** メソッドを使用したセキュリティ チェックをオーバーライドする宣言型の構文を示しています。  この例では、**FileIOPermission** オブジェクトのインスタンスが宣言されています。  許可されるアクセス権の種類を定義するため、コンストラクターに **FileIOPermissionAccess.AllAccess** が渡され、後にファイルの場所を記述した文字列が続きます。  いったん **FileIOPermission** オブジェクトが定義されると、セキュリティ チェックをオーバーライドする際に **Assert** メソッドを呼び出すだけで済みます。  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## 参照  
 <xref:System.Security.PermissionSet>   
 <xref:System.Security.Permissions.SecurityPermission>   
 <xref:System.Security.Permissions.FileIOPermission>   
 <xref:System.Security.Permissions.SecurityAction>   
 [属性](../../../docs/standard/attributes/index.md)   
 [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)