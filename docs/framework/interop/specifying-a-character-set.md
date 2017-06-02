---
title: "文字セットの指定 | Microsoft Docs"
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
  - "属性フィールド (プラットフォーム呼び出しにおける), CharSet"
  - "CharSet フィールド"
  - "プラットフォーム呼び出し, 属性フィールド"
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 文字セットの指定
<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> フィールドは、文字列のマーシャリングを制御したり、プラットフォーム呼び出しで DLL 内の関数名を検索する方法を決定したりします。  このトピックでは、両方の動作について説明します。  
  
 一部の API は、文字列引数がナロー \(ANSI\) とワイド \(Unicode\) の 2 つの関数のバージョンをエクスポートします。  たとえば Win32 API には、**MessageBox** 関数に対して次のエントリ ポイント名が含まれています。  
  
-   **MessageBoxA**  
  
     1 バイト文字 ANSI 形式を提供します。エントリ ポイント名の末尾の "A" で区別されます。  **MessageBoxA** への呼び出しでは、Windows 95 プラットフォームおよび Windows 98 プラットフォームで通常行われているように、文字列は常に ANSI 形式でマーシャリングされます。  
  
-   **MessageBoxW**  
  
     2 バイト文字 Unicode 形式を提供します。エントリ ポイント名の末尾の "W" で区別されます。  **MessageBoxW** への呼び出しでは、Windows NT、Windows 2000、Windows XP の各プラットフォームで通常行われているように、文字列は常に Unicode 形式でマーシャリングされます。  
  
## 文字列のマーシャリングと名前の一致  
 **CharSet** フィールドは、次の値を受け入れます。  
  
 **CharSet.Ansi** \(既定値\)  
  
-   文字列のマーシャリング  
  
     プラットフォーム呼び出しでは、文字列をマネージ形式 \(Unicode\) から ANSI 形式にマーシャリングします。  
  
-   名前の一致  
  
     <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=fullName> フィールドが **true** \([!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] の既定値\) の場合、プラットフォーム呼び出しでは、指定した名前だけが検索されます。  たとえば **MessageBox** と指定すると、プラットフォーム呼び出しでは **MessageBox** を検索し、正確に一致する名前が見つからない場合には失敗します。  
  
     **ExactSpelling** フィールドが **false** \(C\+\+ および C\# の既定値\) の場合、プラットフォーム呼び出しでは、変形処理されていない名前 \(**MessageBox**\) を最初に検索し、それが見つからない場合には、変形処理された名前 \(**MessageBoxA**\) を検索します。  名前の一致の動作は、ANSI と Unicode とでは異なります。  
  
 **CharSet.Unicode**  
  
-   文字列のマーシャリング  
  
     プラットフォーム呼び出しでは、文字列をマネージ形式 \(Unicode\) から Unicode 形式にコピーします。  
  
-   名前の一致  
  
     **フィールドが** true[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] の既定値\) の場合、プラットフォーム呼び出しでは、指定した名前だけが検索されます。  たとえば **MessageBox** と指定すると、プラットフォーム呼び出しでは **MessageBox** を検索し、正確に一致する名前が見つからない場合には失敗します。  
  
     **ExactSpelling** フィールドが **false** \(C\+\+ および C\# の既定値\) の場合、プラットフォーム呼び出しでは、変形処理された名前 \(**MessageBoxW**\) を最初に検索し、それが見つからない場合には、変形処理されていない名前 \(**MessageBox**\) を検索します。  名前の一致の動作は、Unicode と ANSI とでは異なります。  
  
 **CharSet.Auto**  
  
-   プラットフォーム呼び出しでは、対象となるプラットフォームに応じて、実行時に ANSI 形式または Unicode 形式を選択します。  
  
## Visual Basic での文字セットの指定  
 **MessageBox** 関数を 3 回宣言し、そのそれぞれで異なる文字セットを指定する例を次に示します。  Visual Basic で文字セットを指定するには、宣言ステートメントに **Ansi**、**Unicode**、または **Auto** キーワードを追加します。  
  
 この例の最初の宣言ステートメントのように、文字セット キーワードを省略すると、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> フィールドは既定で ANSI 文字セットに設定されます。  この例の第 2 および第 3 のステートメントでは、キーワードを使用して明示的に文字セットを指定しています。  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## C\# および C\+\+ での文字セットの指定  
 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=fullName> フィールドでは、基になる文字セットを ANSI または Unicode として識別します。  この文字セットは、メソッドに対する文字列引数をマーシャリングする方法を制御します。  文字セットを指示するには、次のいずれかの書式を使用します。  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 文字セットを指定する **MessageBox** 関数の 3 種類のマネージ定義の例を次に示します。  最初の定義では、省略によって、**CharSet** フィールドが既定の ANSI 文字セットに設定されます。  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [マネージ コードでのプロトタイプの作成](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [プラットフォーム呼び出しの例](../../../docs/framework/interop/platform-invoke-examples.md)   
 [プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)