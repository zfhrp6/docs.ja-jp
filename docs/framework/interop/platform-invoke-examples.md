---
title: "プラットフォーム呼び出しの例 | Microsoft Docs"
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
  - "COM 相互運用機能, プラットフォーム呼び出し"
  - "DLL 関数"
  - "例 [.NET Framework], プラットフォーム呼び出し"
  - "相互運用 (アンマネージ コードとの), プラットフォーム呼び出し"
  - "プラットフォーム呼び出し, 例"
  - "アンマネージ関数"
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# プラットフォーム呼び出しの例
User32.dll 内の **MessageBox** 関数を定義し、引数として単純な文字列を渡して呼び出す方法の例を次に示します。  この例では、対象となるプラットフォームが文字のバイト幅と文字列のマーシャリング方法を決定できるように、[DllImportAttribute.CharSet Field](frlrfSystemRuntimeInteropServicesDllImportAttributeClassCharSetTopic) フィールドを **Auto** に設定しています。  
  
 同じ内容の例を Visual Basic、C\#、および C\+\+ で示します。  すべての例を表示するには、このページの左上隅にある \[言語のフィルター\] ボタン ![](../../../docs/framework/interop/media/filter2.gif "Filter2") をクリックしてください。  その他の例については、「[プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)」を参照してください。  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
       ByVal caption As String, ByVal Typ As Integer) As IntPtr  
End Class  
  
Public Class HelloWorld      
    Public Shared Sub Main()  
        Win32.MessageBox(0, "Hello World", "Platform Invoke Sample", 0)  
    End Sub  
End Class  
  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
public class Win32 {  
     [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern IntPtr MessageBox(int hWnd, String text,   
                     String caption, uint type);  
}  
  
public class HelloWorld {  
    public static void Main() {  
       Win32.MessageBox(0, "Hello World", "Platform Invoke Sample", 0);  
    }  
}  
  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
  
typedef void* HWND;  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" IntPtr MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
void main(void) {  
     String* pText = L"Hello World!";  
     String* pCaption = L"Platform Invoke Sample";  
     MessageBox(0, pText, pCaption, 0);  
}  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [マネージ コードでのプロトタイプの作成](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [文字セットの指定](../../../docs/framework/interop/specifying-a-character-set.md)