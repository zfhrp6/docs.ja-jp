---
title: "方法 : Windows フォームからビープ音を再生する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "サウンド、ビープ音"
  - "Windows フォームでサウンド"
  - "サウンドの再生"
  - "フォームでサウンド"
  - "サウンドの例 [Windows フォーム]"
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームからビープ音を再生する
この例では、実行時にビープ音を再生します。  
  
## <a name="example"></a>例  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  C# コード サンプルで再生するサウンドが基準、<xref:System.Media.SystemSounds.Beep%2A>システム サウンド設定します。 詳細については、次を参照してください。 <xref:System.Media.SystemSounds>します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 C# の場合、この例への参照が必要です、 <xref:System.Media?displayProperty=fullName>名前空間。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>   
 <xref:System.Media.SoundPlayer>   
 [方法: Windows フォームからシステム サウンドを再生します。](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)   
 [方法: Windows フォームからサウンドを再生](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)