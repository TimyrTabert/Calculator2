# Calculator2
Калькулятор с невидимыми кнопками и меняющимися темами
![Screenshot1](screenshot.png)









package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.content.ContextCompat;

import android.os.Bundle;
import android.text.TextUtils;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.LinearLayout;
import android.widget.SeekBar;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {

    EditText etNum1;
    EditText etNum2;
    Button btnPlus;
    Button btnMinus;
    Button btnUmnojit;
    Button btnDelit;
    Button btnOstatok;
    Button btnStepen;
    Button btnMid;
    TextView tvResult;
    String oper = "";
    LinearLayout mLinearLayout;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        etNum1 = findViewById(R.id.editTextTextPersonName2);
        etNum2 = findViewById(R.id.editTextTextPersonName3);
        btnPlus = findViewById(R.id.button4);
        btnMinus = findViewById(R.id.button);
        btnUmnojit = findViewById(R.id.button3);
        btnDelit = findViewById(R.id.button2);
        btnOstatok = findViewById(R.id.button5);
        btnStepen = findViewById(R.id.button6);
        btnMid = findViewById(R.id.button7);

        mLinearLayout = findViewById(R.id.linearlayout);

        tvResult = findViewById(R.id.textView3);

        btnPlus.setOnClickListener((View.OnClickListener) this);
        btnMinus.setOnClickListener((View.OnClickListener) this);
        btnUmnojit.setOnClickListener((View.OnClickListener) this);
        btnDelit.setOnClickListener((View.OnClickListener) this);
        btnOstatok.setOnClickListener((View.OnClickListener) this);
        btnStepen.setOnClickListener((View.OnClickListener) this);
        btnMid.setOnClickListener((View.OnClickListener) this);
    }

    public void onClick(View v) {
        float num1 = 0;
        float num2 = 0;
        float result = 3;

        if(TextUtils.isEmpty(etNum1.getText().toString()) || TextUtils.isEmpty(etNum2.getText().toString())){
            return;
        }

        num1 = Float.parseFloat(etNum1.getText().toString());
        num2 = Float.parseFloat(etNum2.getText().toString());

        switch (v.getId()){
            case R.id.button4:
                oper = "+";
                result = num1 + num2;
                break;
            case R.id.button:
                oper = "-";
                result = num1 - num2;
                break;
            case  R.id.button3:
                oper = "*";

                result = num1 * num2;
                break;
            case R.id.button2:
                oper = "/";
                if (num2==0)
                {
                    Toast.makeText(this, "ДЕЛИТЬ НА НОЛЬ НЕЛЬЗЯ!", Toast.LENGTH_SHORT).show();
                    result = 0;
                    break;
                }
                result = num1/num2;
                break;
            case R.id.button5:
                oper = "%";
                result = num1 % num2;
                break;

            case R.id.button6:
                oper = "^";
                result = (float) Math.pow(num1, num2);
            case  R.id.button7:
                oper = "и";
                result = (num1 + num2)/2;
        }
        tvResult.setText(num1 + " " + oper + " " + num2 + " = " + result);
    }

    public boolean onCreateOptionsMenu(Menu menu)
    {
        menu.add(0,1,0,"Reset");
        menu.add(0,2,0,"Quit");
        menu.add(0,3,0,"Ostatok");
        menu.add(0,4,0,"White");
        menu.add(0,5,0,"Dark");
        menu.add(0,6,0,"Srednee");
        menu.add(0,7,0,"Teal");
        menu.add(0,8,0,"Purple");
        return super.onCreateOptionsMenu(menu);
    }
    public boolean onOptionsItemSelected(MenuItem item)
    {
        switch (item.getItemId())
        {
            case 1:
                etNum1.setText("");
                etNum2.setText("");
                tvResult.setText("");
                btnOstatok.setVisibility(View.INVISIBLE);
                btnMid.setVisibility(View.INVISIBLE);
                break;
            case 2:
                finish();
                break;
            case 3:
                btnOstatok.setVisibility(View.VISIBLE);
                break;
            case 4:
                mLinearLayout.setBackgroundColor(ContextCompat.getColor(this, R.color.white));
                etNum1.setTextColor(ContextCompat.getColor(this,R.color.black));
                etNum2.setTextColor(ContextCompat.getColor(this,R.color.black));
                tvResult.setTextColor(ContextCompat.getColor(this,R.color.black));
                break;
            case 5:
                mLinearLayout.setBackgroundColor(ContextCompat.getColor(this, R.color.black));
                etNum1.setTextColor(ContextCompat.getColor(this,R.color.white));
                etNum2.setTextColor(ContextCompat.getColor(this,R.color.white));
                tvResult.setTextColor(ContextCompat.getColor(this,R.color.white));
                break;
            case 6:
                btnMid.setVisibility(View.VISIBLE);
                break;
            case 7:
                mLinearLayout.setBackgroundColor(ContextCompat.getColor(this, R.color.teal_200));
                etNum1.setTextColor(ContextCompat.getColor(this,R.color.teal_700));
                etNum2.setTextColor(ContextCompat.getColor(this,R.color.teal_700));
                tvResult.setTextColor(ContextCompat.getColor(this,R.color.teal_700));
                break;
            case 8:
                mLinearLayout.setBackgroundColor(ContextCompat.getColor(this, R.color.purple_200));
                etNum1.setTextColor(ContextCompat.getColor(this,R.color.purple_500));
                etNum2.setTextColor(ContextCompat.getColor(this,R.color.purple_500));
                tvResult.setTextColor(ContextCompat.getColor(this,R.color.purple_500));
                break;

        }
        return super.onOptionsItemSelected(item);
    }
}

