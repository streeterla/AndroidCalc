package de.sms.android.calculator.free;

import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.TextView;

public class CancelButtonListener implements OnClickListener {

	
	/** input field */
	private TextView tv;
	private TextView errorField;
	
	
	/** constructor */
	public CancelButtonListener(TextView tv, TextView errorField)
	{
		this.tv = tv;
		this.errorField = errorField;
	}

	
	/**
	 * function to delete last token
	 */
	public void onClick(View v)
	{
		if((MainActivity.globalSettings.isVibrationOn()))
			MainActivity.myVib.vibrate(MainActivity.globalSettings.getVibrationDensityNumber());
		errorField.setText("");
		CharSequence currentText =  tv.getText();
		if(currentText.length() > 0)
		{
			String newText = currentText.toString().substring(0, currentText.length()-1);
			tv.setText(newText);
			
			//enable calc buttons if deleted token was an arithmetic operator
			char deletedToken = currentText.charAt(currentText.length()-1);
			char[] arithmeticOperators = {'+', '-', '*', '/' };
			for(char arithmeticOperator : arithmeticOperators)
			{
				if(deletedToken == arithmeticOperator)
				{
					for(Button calcButton : MainActivity.getCalcButtons())
					{
						calcButton.setEnabled(true);
					}
				}
			}
		}
	}

}
