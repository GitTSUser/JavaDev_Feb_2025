package com.ford.arrays;

public class Project {

    private int serialNo;
    private String name;
    private String domain;
    private double cost;
    private String manager;
    private int teamSize;
    private String projectStatus;

    public Project(int serialNo,String name,String domain,double cost,String manager,int teamSize,String projectStatus){
        this.serialNo=serialNo;
        this.name=name;
        this.domain=domain;
        this.cost=cost;
        this.manager=manager;
        this.teamSize=teamSize;
        this.projectStatus=projectStatus;
    }

    public int getSerialNo(){
        return this.serialNo;
    }

    public String getName(){
        return this.name;
    }

    public String getDomain(){
        return this.domain;
    }

    public double getCost(){
        return this.cost;
    }

    public String getManager(){
        return this.manager;
    }

    public int getTeamSize(){
        return this.teamSize;
    }

    public String getProjectStatus(){
        return this.projectStatus;
    }

    public void setName(String name){
        this.name=name;
    }

    public void setCost(double cost){
        this.cost=cost;
    }

    public void setSerialNo(int serialNo){
        this.serialNo=serialNo;
    }

    public void setDomain(String domain){
        this.domain=domain;
    }

    public void setManager(String manager){
        this.manager=manager;
    }
    public void setTeamSize(int teamSize){
        this.teamSize=teamSize;
    }
    public void setProjectStatus(String projectStatus){
        this.projectStatus=projectStatus;
    }
}

package com.ford.arrays;

import java.util.Arrays;

public class Main {

    private static Project[] projects;

    static {

        Project project1 = new Project(1, "CMS", "HEALTHCARE", 12, "arun", 5, "IN-PROGRESS");
        Project project2 = new Project(2, "BCMS", "PAYMENT", 15, "tarun", 7, "IN-PROGRESS");
        Project project3 = new Project(3, "MMS", "RAIL-ROAD", 20, "varun", 6, "NEW");
        Project project4 = new Project(4, "CCMS", "HEALTHCARE", 17, "karun", 4, "DONE");
        Project project5 = new Project(5, "KMS", "RAIL-ROAD", 25, "arun", 5, "NEW");

        projects = new Project[]{
                project1, project2, project3, project4, project5
        };

    }

    public boolean findProject(String projectName) {

        for (int i = 0; i < projects.length; i++) {

            Project project = projects[i];

            String projName = project.getName();

            if (projName.equalsIgnoreCase(projectName)) {
                return true;
            }
        }
        return false;
    }

    public void findProjects(String domain) {

        for (int i = 0; i < projects.length; i++) {
            Project project = projects[i];
            String domainName = project.getDomain();

            if (domainName.equalsIgnoreCase(domain)) {

                System.out.println(project.getSerialNo() + " " + project.getName() + " " + project.getDomain() + " " + project.getCost());

            }
        }
    }

    public double findTotalCost(String domain) {

        double totalCost = 0.0;
        for (int i = 0; i < projects.length; i++) {

            Project project = projects[i];
            String projDomain = project.getDomain();

            if (projDomain.equalsIgnoreCase(domain)) {
                double projectCost = project.getCost();
                totalCost = totalCost + projectCost;
            }

        }

        return totalCost;
    }


    public void removeProjects(String status) {

        for (int i = 0; i < projects.length; i++) {

            Project project = projects[i];
            String projStatus = project.getProjectStatus();

            if (projStatus.equalsIgnoreCase(status)) {
                projects[i] = null;
                int j = i;
                do {
                    projects[j] = projects[j + 1];
                    j++;
                } while (j < projects.length - 1);
                projects= Arrays.copyOf(projects,projects.length-1);
            }
        }

    }

    public void printProjectDetails(int teamSize) {

        for(int i=0;i<projects.length;i++){

            Project project=projects[i];

            int projTeamSize=project.getTeamSize();

            if(projTeamSize==teamSize){

                System.out.println(project.getSerialNo()+" "+project.getName()+" "+project.getDomain()+" "+project.getCost()+" "+project.getTeamSize());

            }
        }
    }


    public static void main(String[] args) {

        Main obj=new Main();
        obj.findProjects("RAIL-ROAD");
        double totalCost=obj.findTotalCost("RAIL-ROAD");
        System.out.println("Total cost is:"+totalCost);


        System.out.println("---All projects---");

        for(int i=0;i<projects.length;i++){

            Project p=projects[i];
            System.out.println(p.getSerialNo()+" "+p.getDomain()+" "+p.getProjectStatus());

        }

        obj.removeProjects("DONE");

        System.out.println("---All projects---");

        for(int i=0;i<projects.length;i++){

            Project p=projects[i];
            System.out.println(p.getSerialNo()+" "+p.getDomain()+" "+p.getProjectStatus());

        }



    }
}




