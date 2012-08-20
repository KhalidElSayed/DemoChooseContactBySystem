package com.michael.demo.choosecontactbysys;

import android.app.Activity;
import android.content.Intent;
import android.database.Cursor;
import android.net.Uri;
import android.os.Bundle;
 
import android.provider.ContactsContract.CommonDataKinds.Phone;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;

/**
 * This Demo is For :
 * Choose contact From System Contact Picker Activity.
 * Currently only single selection can be support,if you want to make multiple selection,
 * you should get all the contacts first,then make multiple selection. 
 * 
 * 
 * 这个Demo演示的是如何从系统中选择联系人，但是只能支持单选，如果要多选的话，需要自己将所有的联系人信息加载
 * 然后供用户挑选
 * 
 * */
public class MainActivity extends Activity {

	private static final int CONTACT_PICKER_RESULT = 0; 
	private EditText etShowContact;
    @Override
    public void onCreate(Bundle savedInstanceState) 
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        etShowContact = (EditText)findViewById(R.id.et_show_contact);
        Button button = (Button)findViewById(R.id.btn_choose_contact);
        
        button.setOnClickListener(new OnClickListener() 
        {
			
			@Override
			public void onClick(View v) 
			{
				launchContactPicker();
			}
		});
    }
    
    /**
     * launch System contact picker Activity
     * 
     * 启动系统的挑选联系人的Activity
     * */
    private void launchContactPicker()
    {
    	Intent i = new Intent(Intent.ACTION_PICK);
        i.setType(Phone.CONTENT_TYPE);
        startActivityForResult(i, CONTACT_PICKER_RESULT);
    }

    @Override
    protected void onActivityResult (int requestCode, int resultCode, Intent data) 
    {
        super.onActivityResult(requestCode, resultCode, data);
        
        if(resultCode == RESULT_OK)
        {
        	switch (requestCode) 
        	{
        	//handle the result...
        	//处理返回的结果
            case CONTACT_PICKER_RESULT:
                if (data == null)
                {
                    return;
                }
                Uri uri = data.getData();
                Cursor cursor = getContentResolver().query(uri, null, null, null, null);
                cursor.moveToFirst();
                
                String name = cursor.getString(cursor.getColumnIndexOrThrow(Phone.DISPLAY_NAME));
                String number = cursor.getString(cursor.getColumnIndexOrThrow(Phone.NUMBER));
                
                etShowContact.setText(name + number);
                break;
        	}
        
        }
    } 
    
}
