# My-First-Sudoku-Game
## 
i am trying to create sudoku game with C#
here is the source code

Developing in android for Console
<br>
with(app) = C#Shell - C# Compiler 
```csharp
using System;
using System.IO;
using System.Linq;
using System.Collections.Generic;

namespace SudokuConsole
{

	public class Program
	{
		static string[,] GameTable={
			{"A1","A2","A3","A4","A5","A6","A7","A8","A9"},
			{"B1","B2","B3","B4","B5","B6","B7","B8","B9"},
			{"C1","C2","C3","C4","C5","C6","C7","C8","C9"},
		};
		public static void Main()
		{
			StartGame();

		}
		static void StartGame()
		{
			try
			{
				//ListIntro();
				ListTable();
				while(true){
				ChangeTable(crdln("Point :").ToString().ToUpper(),Convert.ToInt32(crdln("Number :")),true);
				}
			}
			catch
			{

			}
		}

		// Table - Edit Commands
		static void ListTable()
		{
			cwl("\n"+Create_LineStr("=",GameTable.GetLength(1)+29));
			for(int i=0;i<GameTable.GetLength(0);i++)
			{
				for(int j=0;j<GameTable.GetLength(1);j++)
				{
					if(j%3==0 && j!=0){
						cw("=");
					}
					cw("|"+GameTable[i,j]+"|");
				}
				cwl("\n"+Create_LineStr("=",GameTable.GetLength(1)+29));
			}
		}
		
		static int trashPointer=0;
		static void ChangeTable(string pointID,int number,bool autoRefresh)
		{
			try{
				switch(pointID.Substring(0,1).Replace(" ",""))
				{
					case "A":
					trashPointer=Convert.ToInt32(pointID.Substring(1).Replace(" ",""))-1;
					GameTable[0,trashPointer]=" "+number.ToString();
					break;
					
					case "B":
					trashPointer=Convert.ToInt32(pointID.Substring(1).Replace(" ",""))-1;
					GameTable[1,trashPointer]=" "+number.ToString();
					break;
					
					case "C":
					trashPointer=Convert.ToInt32(pointID.Substring(1).Replace(" ",""))-1;
					GameTable[2,trashPointer]=" "+number.ToString();
					break;
				}
				cclear();
				
				if(autoRefresh==true){
					
					ListTable();
					
				}
				
			}catch{
				
			}
		}
		
		// Contact Game-Player
		// console write line
		static void cwl(object msg)
		{
			Console.WriteLine(msg);
		}
		// console write
		static void cw(object msg)
		{
			Console.Write(msg);
		}
		// console read line
		static object crdln(object msg = null)
		{
			Console.Write(msg);
			return Console.ReadLine();
		}
		// console clear
		static void cclear()
		{
			Console.Clear();
		}
		
		// String generator
		static string trashString="";
		static string Create_LineStr(string replayTxt,int txtLength)
		{
			trashString="";
			for(int i=0;i<txtLength;i++)
			{
				trashString+=replayTxt;
			}
			return trashString;
		}
	}
}
```
