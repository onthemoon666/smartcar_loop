# smartcar_loop
void loop(void)//全程循迹
{
	normal_loop();
	if((Get_Decide()== 0)&& time==0) //起跑点
	{normal_loop();time=1;} 
	else if(((Get_Decide()== 19) || (Get_Decide()==20))&& time==1) //第一次分岔口
	{normal_loop();time=2;}
	else if((Get_Decide()== 0)&& time==2) //第二次起跑点
	{normal_loop();time=3;}
	else if(((Get_Decide()== 19) || (Get_Decide()==20))&& time==3) //第二次分岔口
	{
		runMotorDir(RIGHT,FORWARD);
		runMotorDir(LEFT,FORWARD);
		runMotorSpeed(LEFT,500);
		runMotorSpeed(RIGHT,1500);
		HAL_Delay(200);
		time=4;
	}
	else if(((Get_Decide()==0)||(Get_Decide()== 1)||(Get_Decide()== 2)||(Get_Decide()== 3)||(Get_Decide()== 5)||(Get_Decide()== 6))&& time==4) //第二次分岔口的T型岔口
	{
		runMotorDir(RIGHT,FORWARD);
		runMotorDir(LEFT,FORWARD);
		runMotorSpeed(LEFT,500);
		runMotorSpeed(RIGHT,1500);
		HAL_Delay(300);
		time=5;
	}
	else if((Get_Decide()== 0)&& time==5) //终点线
	{
		while(1)
		{
			_stop();
		}
	}
	else 
	{normal_loop();}
	
}
