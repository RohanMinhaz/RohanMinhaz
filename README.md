#include<stdio.h>
#include<conio.h>
#include<string.h>
#include<ctype.h>
#include<stdlib.h>
#include<windows.h>
#include<time.h>

#define ENTER 13
#define BKSP 8
#define SPACE 32
#define TAB 9

void setcolor(int ForgC)
{ WORD wColor;
HANDLE hStdOut=GetStdHandle(STD_OUTPUT_HANDLE);
CONSOLE_SCREEN_BUFFER_INFO csbi;

if(GetConsoleScreenBufferInfo(hStdOut,&csbi))
{
	wColor=(csbi.wAttributes & 0xF0)+(ForgC & 0x0F);
//	SetConsoleTextAttributes(hStdOut,wColor);
	SetConsoleTextAttribute(hStdOut,wColor);

}
}


struct item
{
	char productname[40],productcomp[40],c;
	int productid;
	int price;
	int Qnt;
}st;

void wel_come(void);
void title(void);
void login();
void menu(void);
void title(void);
void deleteproduct(void);
void gotoxy(short x, short y)
{
	COORD pos ={x,y};
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),pos);
}

void add_item();
void read_item();
void search_item();
void edit_item();
void main(void)

{
wel_come(); //call for welcome screen function
login(); //call for login function
}



void wel_come(void)

{
    printf("\n                                                                          ");
    printf("\n                              .-+++                                       ");
    printf("\n                     .     :+****+**:                                     ");
    printf("\n                     .:-=+*+***+++++*=                                    ");
    printf("\n                    -    .:=+++++++++*+.                                  ");
    printf("\n                   ..       .:-++++++++*-                                 ");
    printf("\n                   -            .:=++++++=                                ");
    printf("\n                   :               =+-=+++*:                              ");
    printf("\n                  :       .       .#::::+++++                             ");
    printf("\n                  :      .....    +++**+++++++.                           ");
    printf("\n                 ..  .     .      #=***++++==++:                          ");
    printf("\n                 :     ..        -**+*+++===+=+==                         ");
    printf("\n                .:    .. .. ..   *++**+==++=+====+.                       ");
    printf("\n                :       ..      :#***+=+++=+==+====-                      ");
    printf("\n                -         .. .  ++++*=====++===----.=                     ");
    printf("\n               :     ..        .#-..:*+======---.:+##                     ");
    printf("\n               =     . ..      -*+**#**------:.=*##**.                    ");
    printf("\n              ..        . .    *++++=-##--:.-+##****+=:                   ");
    printf("\n              =           .   :#==+*::=*#:+###*****++-=-                  ");
    printf("\n              :               ++==**-::=*##*****+++==---=.                ");
    printf("\n             -               .#==+#++-:-=#****+++==--:-----               ");
    printf("\n             -               =*=+*#*+=-:=#**++===----:---:-=              ");
    printf("\n            :                #==*#*+===-=#*+===---:::=+=-:--=.            ");
    printf("\n            =               :#+*##*+=====#+=----:::=*#=----::--           ");
    printf("\n           .. .             +=+++*#++====#=-:-::-+##*--:---:::::          ");
    printf("\n           =.              .%+++*#*#++===#--::-*##+:.-:-::::..-#.         ");
    printf("\n          .:  .            =*+---**##++=+*::::*@@% :.::.::..=#+.:         ");
    printf("\n          -. .  . .   . ...#===--+####+***-*##+@@@#.......=#+::::         ");
    printf("\n          -........... . .-%===-+=+##*#***#*:..:%@@*-...+#=::::::         ");
    printf("\n         :................*=-::-**+*##**==:......#@@*-+#=::::::::         ");
    printf("\n         =.....:.........:#--=+=+=--=***::.... :+*@@#=+::::::::::         ");
    printf("\n        .:........:......=+===*+=#::.-*-:... :*#=:@@#=-::::::::::.        ");
    printf("\n        =.:..::.........:#==+*#**+#.:::... -##-:::%@#--::::::::::.        ");
    printf("\n        =::.::::.:......=#=+*#***#*%.....-#*-:::::+@#-:::::::::-:         ");
    printf("\n       -:::::::::::....:*=+*#%#####*#..=#*-:::::::-@#-:::::::-:.          ");
    printf("\n       +:::::::::::::..-#-+**#######*=#+::::::::::-@#::::::-:.            ");
    printf("\n       +*=:::::::::::::++=++++######*=-:::::::::::-%*::::--.              ");
    printf("\n       :-=*+-::::::::::#-=+++=*##**##::::::::::::::++::--.                ");
    printf("\n       :---:+*=:--::::=*=++*==-+*****:::::::::::::-::--.                  ");
    printf("\n       .---=-:-++=----*=+=++--::+++++:::::::::::-:                        ");
    printf("\n        :======--=*+==#-====:::::=+==:::::::::-:                          ");
    printf("\n         :-=======--+*+--==::::..:===:::::::-:.                           ");
    printf("\n         ..:-=++====--:--=-:......:=-::::--:.                             ");
    printf("\n         ....::=+++===---=:........:=:::-:.                               ");
    printf("\n         .......::=+++=--=..........::-:                                  ");
    printf("\n           ........:=++=-:....       ..                                   ");
    printf("\n             .........:==..                                               ");
    printf("\n                 ........                                                 ");
    printf("\n                    ...                                                   ");

    sleep(3);


    printf("\n        ######  #     # ######  #######     #####  ####### #       ######     #       ####### ######       ");
    printf("\n        #     # #     # #     # #          #     # #     # #       #     #    #          #    #     #      ");
    printf("\n        #     # #     # #     # #          #       #     # #       #     #    #          #    #     #      ");
    printf("\n        ######  #     # ######  #####      #  #### #     # #       #     #    #          #    #     #      ");
    printf("\n        #       #     # #   #   #          #     # #     # #       #     #    #          #    #     # ###  ");
    printf("\n        #       #     # #    #  #          #     # #     # #       #     #    #          #    #     # ###  ");
    printf("\n        #        #####  #     # #######     #####  ####### ####### ######     #######    #    ######  ###  ");

    sleep(3);
	time_t t;
	time(&t);
	printf("                                                                                                         \n");
	printf("---------------------------------------------------------------------------------------------------------\n");
	printf("\t\t\t\t\t%s",ctime(&t));
	printf("---------------------------------------------------------------------------------------------------------\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t==================================\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t|\t     WELCOME TO \t |\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t|\t   PURE GOLD LTD.    \t |\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t==================================\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t   address:New Market,Dhaka    \t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t            OUR MOTTO      \t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t      \"WE BELIEVE IN PURITY\"\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|\t\t\t\t\t\t\t\t\t\t\t\t\t\t|\n");
	printf("|Press any key to continue.........\t\t\t\t\t\t\t\t\t\t|\n");

	printf("---------------------------------------------------------------------------------------------------------\n");

getch();
system("cls");
}
